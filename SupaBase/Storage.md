
# Storage
  it is store your image , video in the supavase server 


![스크린샷 2025-07-07 오후 8 25 25](https://github.com/user-attachments/assets/1a97e01f-50ce-4123-b833-77f1f63e5c49)  
![스크린샷 2025-07-07 오후 8 25 44](https://github.com/user-attachments/assets/d00e46a1-2a8f-469c-a864-c265c898972c)  
![스크린샷 2025-07-07 오후 8 28 10](https://github.com/user-attachments/assets/fef62b17-5844-407b-9a81-c20ca217db8a)
![스크린샷 2025-07-07 오후 8 28 26](https://github.com/user-attachments/assets/419031d6-586b-48cf-83d2-98ea5a85ec6c)
![스크린샷 2025-07-07 오후 8 28 54](https://github.com/user-attachments/assets/50d5ea4f-74d3-4bc4-a819-e965ba23eb20)
![스크린샷 2025-07-07 오후 8 30 05](https://github.com/user-attachments/assets/e5fc9aa5-42ca-40c7-8919-53352f3c4c0c)
![스크린샷 2025-07-07 오후 8 30 36](https://github.com/user-attachments/assets/7882fa21-f80a-4cc5-9b5e-fbab66823e6d)



##  input form 


```typescript
 const fileRef = useRef(null); //  Access input dom



 const uploadImageMutation = useMutation({   
   mutationFn: uploadFile,
   onSuccess: () => {
      queryClient.invalidateQueries({   // refetch your new image 
        queryKey:["images"],
      });
   }
 })



  <form onSubmit={ async (e)=>{
        e.preventDefault();
    
        const file = fileRef.current.files?.[0];
        
        const formData = new FormData();
        
        formData.append('file',file);


         const result = await uploadImageMutation.mutate(formData); 
    }}
      className="w-full py-20 border-4 border-dotted border-indigo-700 flex flex-col">
      
      <input ref={fileRef} type="file" />
      
      <p>파일을 업로드하세요.</p>
       
      <Button type="submit">파일 업로드</Button>
    </form>


```





##  serverAction.ts


```typescript
 

export async function uploadFile(formData : FormData)  {
    const supabase = await createServerSupabaseClient();
    
    const file = formData.get('file') as File;

    const {data, error} = await supabase.storage.from(process.env.NEXT_PUBLIC_STORAGE_BUCKET)
    .upload(file.name,file,{upsert:true});

    handleError(error);

    return data;

}

```
