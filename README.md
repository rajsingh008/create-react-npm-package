
# Instructions for creating a new npm package and publishing it to your organization's DevOps Artifacts or npmjs

**Step1** : Create a new folder called “package” in your local drive  and open it in VS Code

**Step2 **: Run Following command in Terminal   “npm init -y “  to install package.config and update following values in package.config file
 
    { 
    "name": "test-unw-react-package", # Your Package name  
    "version": "0.0.2",               # Your Package version 
    "description": "", 
    "main": "./dist/index.js",        # Add folder called dist and add reference here 
    "module": "./dist/index.mjs",     # Add These lines of code 
    "types": "./dist/index.d.ts", 
    "scripts": { 
      "build": "tsup"                 # Replace value with tsup 
    },<br>
    "keywords": [ 
      "test", 
      "unw" 
    ], 
    "author": "", 
    "license": "MIT", 
    "devDependencies": { 
      "tsup": "^8.0.2", 
      "typescript": "^5.3.3" 
      }
    } 

Step 3: Run command “npm install -g typescript” to install typescript as global level

Step 4: Now Run “npm install -D  typescript tsup” to install tsup

Step 5: Add 2 files named as  “tsconfig.json” and “tsup.config.ts” and add following values in each file 

      tsconfig.json:
        {
        "compilerOptions": { 
            "strict": true, 
            "noImplicitAny": true, 
            "esModuleInterop": true, 
            "strictNullChecks": true, 
            "target": "ES2022", 
            "moduleResolution": "Node10", 
            "module": "CommonJS", 
            "declaration": true, 
            "isolatedModules": true, 
            "noEmit": true, 
            "outDir": "dist" 
        },
        "include": ["src"], 
        "exclude": ["node_modules"] 
        }<br>

    tsup.config.ts: 
    import { defineConfig } from 'tsup'; 
  
    export default defineConfig({ 
    format: ['cjs', 'esm'], 
    entry: ['./src/index.ts'], 
    dts: true,<br>
    shims: true,<br>
    skipNodeModulesBundle: true, 
    clean: true, 
    }); 



Step 6: Add new folder “src” and new file “index.ts”.Now add basic code in index.ts file

    export function SayHello(){
    //
    }

Step 7: Now run the command at terminal : “npm run build” this should create your package

Step 8: Add “.gitignore” , “.npmignore” and “README.md” files add following values into it
 
    .gitignore:
        /dist
        /node_modules
        .env
        
    .npmignore:
        /src
        /node_modules
        .env
        tsconfig.json
        tsup.config.ts
    <br>
    README.md:
        # Say hello to my first NPM package
        This is a test package. So ignore it :)

Step 9: Run "npm publish" command in terminal. For new user it will ask to run "add user" command which will open a registration process in npm.js website and once completed re-run the "npm publish" command.

    Existing users can simply log in to access the website and publish their packages.

Once published open browser and check latest package deployed on your npmjs website .

![image](https://github.com/rajsingh008/package/assets/13310226/b57cfd04-8f4e-43ed-99c0-b18801669cca)

# Publish npm package in  DevOps

Add a .npmrc to your project, in the same directory as your package.json and add follwing code in the file

    registry=***DevOps Artifacts registry  URL **
                    
    always-auth=true

Run Follwing Command in terminal 
 
    “npm install -g vsts-npm-auth --registry https://registry.npmjs.com --always-auth false” 

Then, run vsts-npm-auth to get an Azure Artifacts token added to your user-level .npmrc file

    vsts-npm-auth -config .npmrc
  
Now run Follwing command to publish your package to DevOps

    npm publish 

It will publish your package to DevOps artifacts

![image](https://github.com/rajsingh008/create-react-npm-package/assets/13310226/9ca0a66e-c0c8-457b-83d2-feb9a6635301)




