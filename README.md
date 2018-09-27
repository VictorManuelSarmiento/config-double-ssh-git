# config-double-ssh
Instrucciones para configurar una doble clave ssh

## Crear fichero con la nueva clave ssh:

* Ir al directorio: 
`~/.ssh`
* Crear ficheros con la nueva clave ssh (nos solicitara un nombre de fichero): 
` ssh-keygen -t rsa `

## En el directorio .ssh tendremos varios ficheros:

* config
* id_rsa
* id_rsa.pub
* grunmir_rsa
* grunmir_rsa.pub

## Editamos el archivo ~/.ssh/config

```html
Host grunmir
    Hostname github.com
    User git
    IdentityFile /Users/grunmir/.ssh/grunmir_rsa
    IdentitiesOnly yes
Host default
    Hostname github.com
    User git
    IdentityFile /Users/grunmir/.ssh/id_rsa
    IdentitiesOnly yes
```

* __Host__: Un nombre que queramos para identificar la cuenta. Este nombre va a reemplazar el __Hostname__ y el nombre de usuario en la dirección git.
* __Hostname__: El host del repositorio: Bitbucket (bitbucket.org), Github (github.com), etc. Recuerda, es el nombre del host, no la url.

## Como usar la cuenta

Para usar la clave ssh correpondiente a un host hay que cambiar el __remote__ de nuestro proyector por uno nuevo:

* Si `git remote -v` es `git@github.com:grunmir/nombre-repositorio.git`
* Entonces hay que sustituirlo por `git@grunmir:grunmir/nombre-repositorio.git`

De esta forma usaremos la __clave ssh__ correspondiente al __Host__ que hayamos sustituido en la direccion del __remote__ del proyecto.
