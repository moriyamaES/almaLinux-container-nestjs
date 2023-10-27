# almaLinux-container-nestjs
 AlmaLinuxのコンテナにNestjsをインストールする

## Almalinux のコンテナの起動

- 以下のコマンドを実行する

    ```sh
    $ podman pull almalinux:8.8
    ```

    ```sh
    $ podman images | grep almalinux
    docker.io/library/almalinux  8.8         d7d33dffea34  3 months ago  196 MB
    ```

    ```sh
    $ sudo podman run -h almalinux --name almalinux it almalinux:8.8 bash
    Resolved "almalinux" as an alias (/etc/containers/registries.conf.d/000-shortnames.conf)
    Trying to pull docker.io/library/almalinux:8.8...
    Getting image source signatures
    Copying blob 338a80bc21c9 done  
    Copying config d7d33dffea done  
    Writing manifest to image destination    
    ```
## nodejsとnpmのインストール

    ```sh
    [root@almalinux /]# dnf  list --available | egrep "^node"
    nodejs.x86_64                                          1:10.24.0-1.module_el8.3.0+2047+b07ac28e                   appstream
    nodejs-devel.x86_64                                    1:10.24.0-1.module_el8.3.0+2047+b07ac28e                   appstream
    nodejs-docs.noarch                                     1:10.24.0-1.module_el8.3.0+2047+b07ac28e                   appstream
    nodejs-full-i18n.x86_64                                1:10.24.0-1.module_el8.3.0+2047+b07ac28e                   appstream
    nodejs-nodemon.noarch                                  1.18.3-1.module_el8.3.0+2047+b07ac28e                      appstream
    nodejs-packaging.noarch                                17-3.module_el8.3.0+2047+b07ac28e                          appstream
    ```

    ```sh
    [root@almalinux /]# dnf  list --available | egrep "^node"
    nodejs.x86_64                                          1:10.24.0-1.module_el8.3.0+2047+b07ac28e                   appstream
    nodejs-devel.x86_64                                    1:10.24.0-1.module_el8.3.0+2047+b07ac28e                   appstream
    nodejs-docs.noarch                                     1:10.24.0-1.module_el8.3.0+2047+b07ac28e                   appstream
    nodejs-full-i18n.x86_64                                1:10.24.0-1.module_el8.3.0+2047+b07ac28e                   appstream
    nodejs-nodemon.noarch                                  1.18.3-1.module_el8.3.0+2047+b07ac28e                      appstream
    nodejs-packaging.noarch                                17-3.module_el8.3.0+2047+b07ac28e                          appstream
    ```

    ```sh
    [root@almalinux /]# dnf module list nodejs
    ```

    ```sh
    [root@almalinux /]# node -v
    v18.18.2
    ```

    ```sh
    [root@almalinux /]# npm -v
    9.8.1
    ```

## nesutjsのインストール

- インストール可能なバージョンの確認

    ```sh
    [root@almalinux /]# npm info @nestjs/cli

    @nestjs/cli@10.2.0 | MIT | deps: 23 | versions: 211
    Nest - modern, fast, powerful node.js web framework (@cli)
    https://github.com/nestjs/nest-cli#readme

    bin: nest

    dist
    .tarball: https://registry.npmjs.org/@nestjs/cli/-/cli-10.2.0.tgz
    .shasum: 7202a8e594013b1d8a679e7ce2e10fa2e31cb661
    .integrity: sha512-OMbn6A/YNu7QSk1nM8VucrtUwocaa0XEa9uoqRpw5Acvh/KIetvMHCn8L6yIBxiK7yvYiKa8q9U+RpLsKpKfgw==
    .unpackedSize: 241.0 kB

    dependencies:
    @angular-devkit/core: 16.2.7           fork-ts-checker-webpack-plugin: 9.0.0  source-map-support: 0.5.21             
    @angular-devkit/schematics-cli: 16.2.7 glob: 10.3.4                           tree-kill: 1.2.2                       
    @angular-devkit/schematics: 16.2.7     inquirer: 8.2.6                        tsconfig-paths-webpack-plugin: 4.1.0   
    @nestjs/schematics: ^10.0.1            node-emoji: 1.11.0                     tsconfig-paths: 4.2.0                  
    chalk: 4.1.2                           ora: 5.4.1                             typescript: 5.2.2                      
    chokidar: 3.5.3                        os-name: 4.0.1                         webpack-node-externals: 3.0.0          
    cli-table3: 0.6.3                      rimraf: 4.4.1                          webpack: 5.89.0                        
    commander: 4.1.1                       shelljs: 0.8.5                         

    maintainers:
    - nestjscore <admin@kamilmysliwiec.com>
    - kamilmysliwiec <mail@kamilmysliwiec.com>

    dist-tags:
    latest: 10.2.0       next: 10.1.0-next.3  

    published 4 days ago by nestjscore <admin@kamilmysliwiec.com>
    npm notice 
    npm notice New major version of npm available! 9.8.1 -> 10.2.1
    npm notice Changelog: https://github.com/npm/cli/releases/tag/v10.2.1
    npm notice Run npm install -g npm@10.2.1 to update!
    npm notice 
    ```

    ```sh
    [root@almalinux /]# npm i -g @nestjs/cli

    added 283 packages in 21s

    55 packages are looking for funding
    run `npm fund` for details
    ```

- インストールできた！！

