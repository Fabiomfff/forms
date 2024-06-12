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

compressão gzip
    Run npm install -g gzipper to install gzipper globally
    Run ng build --prod or your build script in angular project
    Run gzipper compress ./dist to compress the files in dist folder
    Note: Enable gzip compression on server end


--------------------------------------------------------------- > 

botão com efeito de vidro


.button-manual {
    background-color: transparent;
    display: flex;
    flex-direction: column;
    justify-content: center;
    color: rgb(255, 255, 255);
    box-shadow: none;
    letter-spacing: 3px;
    position: relative; /* Required for the pseudo-element positioning */
    overflow: hidden; 
    transition: all 0.4s ease 0.2s;
}

.button-manual:hover {
    background-color: rgba(255, 255, 255, 0.2); /* Semi-transparent white */
    backdrop-filter: blur(10px); /* Apply blur effect */
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2), 0 6px 20px rgba(0, 0, 0, 0.19); /* Light reflection effect */
}

.button-manual::before {
    content: '';
    position: absolute;
    top: 50%;
    left: -50%;
    width: 0;
    height: 25px;
    background: rgba(255, 255, 255, 0.775); /* Light line color */
    transform: translateY(-50%) rotate(45deg); /* Rotate the line to make it diagonal */
    transition: left 1s ease, width 1s ease;
}


.button-manual:hover::before {
    left: 70%;
    width: 400%;
}
