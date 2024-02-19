# Say hello to my first NPM package 

This is a test package. So ignore it :)

# Steps to create new npm package and publish it in to your orgnizations DevOps Artifacts or in npmjs

**Step1** : Create a new folder called “package” in your local drive  and open it in VS Code

**Step2 **: Run Following command in Termonal  “npm init -y “ to install package.config and update following values in package.config file
{
  "name": "test-unw-react-package", # Your Package name
  "version": "0.0.2",               # Your Package version
  "description": "",
  "main": "./dist/index.js",        # Add folder called dist and add reference here
  "module": "./dist/index.mjs",     # Add These lines of code
  "types": "./dist/index.d.ts",
  "scripts": {
    "build": "tsup"                 # Replace value with tsup
  },
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
}

tsup.config.ts:
import { defineConfig } from 'tsup';
 
export default defineConfig({
    format: ['cjs', 'esm'],
    entry: ['./src/index.ts'],
    dts: true,
    shims: true,
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

README.md:
    # Say hello to my first NPM package
    This is a test package. So ignore it :)

Step 9: Run "npm publish" command in terminal. For new user it will ask to run "add user" command which will open a registration process in npm.js website and once completed re-run the "npm publish" command.

    For existing users login option can be used to login to the website and publish you package.

Once published open browser and check latest package deployed on you npmjs website .

![image](https://github.com/rajsingh008/package/assets/13310226/b57cfd04-8f4e-43ed-99c0-b18801669cca)




