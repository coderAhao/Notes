###### 基础命令

- npm init vite-app projectname  使用npm生成项目
- npm init @vitejs/app 或npm init vite 可以进行详细配置生成项目，包括名字、框架之类的
- yarn create vite-app projectname 使用yarn生成项目
- 如果要创建react项目，需要提前创建好项目文件夹，然后进入到文件夹内部，执行npm init vite-app --template react
- 使用vite跑起项目后，局域网地址不再显示，因此需配置显示
    - 在package.json中，将“dev”的映射命令增加“--host”
    - 如`"dev": "vite"`改为`"dev":"vite --host"`