## Create Table 


1. Find Table Editor  
   <img width="220" alt="스크린샷 2025-07-05 오후 3 23 19" src="https://github.com/user-attachments/assets/9fa5cc73-330c-49c2-990e-9755b5ee4019" />



2. Create Table  
   <img width="702" alt="스크린샷 2025-07-05 오후 3 23 41" src="https://github.com/user-attachments/assets/71d38b85-2c07-485c-9228-cd2dbaa551ea" />
   <img width="664" alt="스크린샷 2025-07-05 오후 3 23 57" src="https://github.com/user-attachments/assets/460329a1-8dc0-40cd-9c92-43df82b847bb" />
   <img width="1129" alt="스크린샷 2025-07-05 오후 3 29 34" src="https://github.com/user-attachments/assets/53836782-701f-4116-9aa7-4b7d4a2b0a6a" />



## Connect Vscode 


1. Make .env file
 ```typescript
 NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
NEXT_SUPABASE_SERVICE_ROLE=
NEXT_SUPABASE_DB_PASSWORD=
```

2.  add "generate-types": in scripts file 
 ```typescript
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "generate-types": "npx supabase gen types typescript --project-id garzzsiryphmrhqfgpgt --schema public > types_db.ts"
  },
```






3. login supabase in the vscode

```bash
npx supabase login
```

4. run generate-types
```bash
npm run generate-types
```


5. check types_db.ts file

 ```typescript
  ToDo: {
        Row: {
          completed: boolean
          created_at: string
          id: number
          title: string
          updated_at: string | null
        }
```




