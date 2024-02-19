# Say hello to my first NPM package 

This is a test package. So ignore it :)

# Instructions for creating a new npm package and publishing it to your organization's DevOps Artifacts or npmjs

**Step1** : Create a new folder called “package” in your local drive  and open it in VS Code

**Step2 **: Run Following command in Terminal   “npm init -y “  to install package.config and update following values in package.config file
<br>
{<br>
  "name": "test-unw-react-package", # Your Package name <br>
  "version": "0.0.2",               # Your Package version<br>
  "description": "",<br>
  "main": "./dist/index.js",        # Add folder called dist and add reference here<br>
  "module": "./dist/index.mjs",     # Add These lines of code<br>
  "types": "./dist/index.d.ts",<br>
  "scripts": {<br>
    "build": "tsup"                 # Replace value with tsup<br>
  },<br>
  "keywords": [<br>
    "test",<br>
    "unw"<br>
  ],<br>
  "author": "",<br>
  "license": "MIT",<br>
  "devDependencies": {<br>
    "tsup": "^8.0.2",<br>
    "typescript": "^5.3.3"<br>
  }<br>
}<br>

Step 3: Run command “npm install -g typescript” to install typescript as global level

Step 4: Now Run “npm install -D  typescript tsup” to install tsup

Step 5: Add 2 files named as  “tsconfig.json” and “tsup.config.ts” and add following values in each file 
tsconfig.json:<br>
{<br>
    "compilerOptions": {<br>
        "strict": true,<br>
        "noImplicitAny": true,<br>
        "esModuleInterop": true,<br>
        "strictNullChecks": true,<br>
        "target": "ES2022",<br>
        "moduleResolution": "Node10",<br>
        "module": "CommonJS",<br>
        "declaration": true,<br>
        "isolatedModules": true,<br>
        "noEmit": true,<br>
        "outDir": "dist"<br>
    },
    "include": ["src"],<br>
    "exclude": ["node_modules"]<br>
}<br>

tsup.config.ts:<br>
import { defineConfig } from 'tsup';<br>
 <br>
export default defineConfig({<br>
    format: ['cjs', 'esm'],<br>
    entry: ['./src/index.ts'],<br>
    dts: true,<br>
    shims: true,<br>
    skipNodeModulesBundle: true,<br>
    clean: true,<br>
});<br>



Step 6: Add new folder “src” and new file “index.ts”.Now add basic code in index.ts file
export function SayHello(){<br>
//<br>
}
<br>
Step 7: Now run the command at terminal : “npm run build” this should create your package

Step 8: Add “.gitignore” , “.npmignore” and “README.md” files add following values into it
 
.gitignore:<br>
    /dist<br>
    /node_modules<br>
    .env
<br>

.npmignore:<br>
    /src<br>
    /node_modules<br>
    .env
    tsconfig.json<br>
    tsup.config.ts<br>
<br>
README.md:<br>
    # Say hello to my first NPM package<br>
    This is a test package. So ignore it :)<br>

Step 9: Run "npm publish" command in terminal. For new user it will ask to run "add user" command which will open a registration process in npm.js website and once completed re-run the "npm publish" command.

    For existing users login option can be used to login to the website and publish you package.

Once published open browser and check latest package deployed on your npmjs website .

![image](https://github.com/rajsingh008/package/assets/13310226/b57cfd04-8f4e-43ed-99c0-b18801669cca)




