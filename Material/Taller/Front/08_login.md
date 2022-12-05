# Crear login 

## 1. Crear el directorio User del componente para la funcionalidad de login y la interfaz user

![image](https://user-images.githubusercontent.com/31961588/205515501-044e5043-9320-40c3-ad68-95c7a4411fc6.png)

## 2. Crear el servicio de autenticación dentro de directorio user

![image](https://user-images.githubusercontent.com/31961588/205515645-32fed1e1-9e65-4d68-9844-14da57e3be4e.png)

## 3. En auth.services.ts importar las librerias necesarias

```TypeScript
import { Injectable } from '@angular/core';
import { Observable } from 'rxjs';
import { HttpClient,HttpHeaders } from '@angular/common/http';
import { User } from './user';
import { environment } from 'src/environments/environment';


@Injectable({
  providedIn: 'root'
})
export class AuthService {

  private _token: string='';
  private _usuario?: User;
  private urlApi: string ='';
  constructor(private http:HttpClient) {
      this.urlApi=environment.apiUrl+'/api';
    
   }

   public get usuario(): User {
      if (this._usuario != null) {
        return this._usuario;
      } else if (this._usuario == null && sessionStorage.getItem('user') != null) {
        this._usuario = JSON.parse(sessionStorage.getItem('user') || '') as User;
        return this._usuario;
      }
      return new User();
    }

   public get token(): string {
      if (this._token != null) {
        return this._token;
      } else if (this._token == null && sessionStorage.getItem('token') != null) {
        this._token = sessionStorage.getItem('token') || '';
        return this._token;
      }
      return this._token;
   }

   isAuthenticated(): boolean{
       if(this._token.length>0 && this._token!=''){
          return true;
       }else{
         return false;
       }

   }

  login(user:User): Observable<any>{
     const urlEnpoint=this.urlApi+'/auth/login';
     return this.http.post<any>(urlEnpoint,user);
  }

  guardarUser(user: User): void {
   this._usuario = new User();
   this._usuario=user;  
   sessionStorage.setItem('user', JSON.stringify(this._usuario));
 }

  guardarToken(accesToken:string): void{
    this._token=accesToken;
    sessionStorage.setItem('token',accesToken);
  }


}

```

## 3. Crear el component login

![image](https://user-images.githubusercontent.com/31961588/205517557-710e302d-80a6-436b-a579-b9f8e9ac757b.png)

## 4. Crear el servicio login.component.ts

```TypeScript
import { Component, OnInit } from '@angular/core';
import { User } from './user';
import { AuthService } from './auth.service';
import { Router } from '@angular/router';

@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css']
})
export class LoginComponent implements OnInit {

  titulo:string='Por favir sing in!';
  user:User;
  constructor(private authService:AuthService,
              private router:Router) {
               this.user=new User();

               }

  ngOnInit(): void {
  }

  login(): void{
     this.authService.login(this.user).subscribe({
      next:(result:any)=>{
        console.log(result);
        this.authService.guardarToken(result.token);
        this.authService.guardarUser(result.usuario);
        this.router.navigate(['/clients']);
     }
     });
  }

}
```

## 5 login.component.html

```Html
<div class="card border-primary text-center" style="width: 40%; margin: 10px auto auto;">
    <div class="card-header">{{titulo}}</div>
    <div class="card-body">
  
      <form method="post"> 
        <div class="form-group col-sm-6">
          <input [(ngModel)]="user.correo" type="text" class="form-control"
          name="correo" id="correo" placeholder="Correo" autofocus style="display:inline; width:400px;"  required>
        </div>
  
        <div class="form-group col-sm-6">
          <input [(ngModel)]="user.password" type="password" class="form-control"
          name="password" id="password" placeholder="Password" style="display:inline; width:400px; margin-top: 10px;" required>
        </div>
  
        <div class="form-group col-sm-6">
          <input (click)='login()' type="submit" class="btn btn-lg btn-primary btn-block" style="display:inline; width:400px; margin-top: 10px;" value="Login">
        </div>
      </form>
    </div>
  </div>
```

## 6. Crear guarda

![image](https://user-images.githubusercontent.com/31961588/205525269-93d4388b-9eca-4aaa-8f2d-8d7d218c23cc.png)

## 7. auth.guard.ts

```TypeScript
import { Injectable } from '@angular/core';
import { Router, ActivatedRouteSnapshot, CanActivate, RouterStateSnapshot, UrlTree } from '@angular/router';
import { Observable } from 'rxjs';
import { AuthService } from './auth.service';

@Injectable({
  providedIn: 'root'
})
export class AuthGuard implements CanActivate {

  constructor(private authService: AuthService,
              private router:Router){}

  canActivate(
    route: ActivatedRouteSnapshot,
    state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {
    if(this.authService.isAuthenticated()){
      return true;
    }
    this.router.navigate(['/login'])
    return false;
  }
  
}
```

## 8. Crear interceptor

![image](https://user-images.githubusercontent.com/31961588/205524370-8e5bd88b-8db5-4a2f-b1ad-1d91e5ecaa84.png)

## 8. user.interceptor.ts

```TypeScript
import { Injectable } from '@angular/core';
import {
  HttpRequest,
  HttpHandler,
  HttpEvent,
  HttpInterceptor
} from '@angular/common/http';
import { Observable } from 'rxjs';
import { AuthService } from './auth.service';

@Injectable()
export class UserInterceptor implements HttpInterceptor {

  constructor(private authService: AuthService) {}

  intercept(request: HttpRequest<unknown>, next: HttpHandler): Observable<HttpEvent<unknown>> {
    let token = this.authService.token;

    if(token!=null){
       const authReq=request.clone({
         headers: request.headers.set('x-token',token)
       });
       return next.handle(authReq);
    }

    return next.handle(request);
  }
}

```

## 9. Ajuste de app-roting

![image](https://user-images.githubusercontent.com/31961588/205529368-0785410a-3222-4624-ae94-4f76b7c1600f.png)

## 10. Ajuste de app.module

![image](https://user-images.githubusercontent.com/31961588/205529464-b18b310e-d808-405f-9245-b927ab72f516.png)

