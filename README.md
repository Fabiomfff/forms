# Importantes 
Arrumar angular pra nova maquina -----------------------------
> install angular, angular schematics, snippets, auto import, better align, git graph, atom on dark theme//
> ng new my-app-name --no-standalone --routing --ssr=false 
> ng add ng add ngx-bootstrap e npm install bootstrap

> ir no arquivo angular.json, colocar nos styles: 
> "styles": [
    "node_modules/bootstrap/dist/css/bootstrap.min.css",
    "src/styles.css"


--------------------------------------------------------------
>Aqui tem um jeito pra verificar token no localstorage, talvez fazer um serviço que faça isso seja uma opção melhor.

>tokenExpired pega uma string do token, faz umas paradas pra pegar a parte final que tem o exp (expires)
>dps mete uma matematica pra pegar a data de expiração
        private tokenExpired(token: any) {
            const expiry = (JSON.parse(atob(token.split('.')[1]))).exp;
            return (Math.floor((new Date).getTime() / 1000)) >= expiry;
        };
>quando a pagina iniciar, ve se o token esta expirado, se esta adiciona a logica dps...
>
        ngOnInit() {
            if(localStorage.getItem('token')){
                if(this.tokenExpired(localStorage.getItem('token'))){
                //logica token expirado.
                    this.isLogged = false;
                    console.log('checking token...')
                    setTimeout(() => {
                        localStorage.clear();
                        console.log('token expirado', (localStorage.getItem('token')))
                        this.route.navigate(['']);
                    }, 3000);
                };
            };

-------------------------------- > ----------------------------------------------->
colocar a poha de um background scrollbars
<div class="bg-image" style="background-image: 
        url('../../assets/algumaImagemQueVoceQuiser.xx'); 
        height: 100vh; 
        background-size: cover; 
        background-position: center;
        vertical-align: top;"> <header e router-outlet> 
</div>

