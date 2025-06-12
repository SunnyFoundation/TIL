* `npm i @types/node `



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;TypeScript requires @types/node to use Node.js's built-in modules.


* `sudo npm install typescript -g `

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; You can use TypeScript And TypeScript compiler  all over your file 


* `tsc -v`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; You can check that installed your typescript compiler




* `sudo npm i -g tsx`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  you can excuted ts file without compile so it is super fast 



* `sudo npm i -g tsx -v`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  version of tsx 



* `tsx src/index.ts
`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  excuted your ts file 



* ` tsc --init
`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  you can manage your ts file with tsconfig.json




```typescript

{
  "compilerOptions": {
    "target": "esnext",  //   Version of JS 
    "module": "esnext",  // what would you use Module Syetem?
    "skipLibCheck": true, // Don't check *.d.ts file 
    "outDir": "dist",  // .js file move into the dist folder 
    "strict": false,  // Check Type 
    "moduleDetection": "force"  // TypeScript manage all of your file Gloval And we don't want to 
  },
  "include": [
    "src/**/*" // you can compile all of your file in the src folder  command tsc  
  ],
}


```
