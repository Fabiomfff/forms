# forms
> install angular, angular schematics, snippets, auto import, better align, git graph, atom on dark theme//
> ng new my-app-name --no-standalone --routing --ssr=false 
> ng add ng add ngx-bootstrap e npm install bootstrap

> ir no arquivo index.hmtl
<body>
  <app-root></app-root>
  <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet">
</body>

> Criar 2 components ( ng g c dataForm  / ng g c templateForm )
> no app.component
--------------------------------------------------------------
<nav class="navbar navbar-default">
    <div class="container-fluid">

        <div class="navbar-header">
            <a class="navbar-brand" routerLink="">Angular Forms</a>
        </div>

        <ul class="nav navbar-nav">
            <li routerLinkActive="active">
                <a routerLink="/templateForm">Form - Template Driven</a>
            </li>
            <li routerLinkActive="active">
                <a routerLink="/dataForm">Form - Data Driven</a>
            </li>
        </ul>
    </div>
</nav>

<div class="container">
    <router-outlet></router-outlet>
</div>
--------------------------------------------------------------
> e depois no app routing module 

import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { TemplateFormComponent } from './template-form/template-form.component';
import { DataFormComponent } from './data-form/data-form.component';

const routes: Routes = [
    { path: 'templateForm', component: TemplateFormComponent},
    { path: 'dataForm', component: DataFormComponent },
    { path: '', redirectTo: 'templateForm', pathMatch: 'full'}
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
--------------------------------------------------------------
