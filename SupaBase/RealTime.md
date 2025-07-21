


##  1. RealTime Setting

### Go To Table Editor

<img width="297" height="337" alt="스크린샷 2025-07-10 오후 7 30 27" src="https://github.com/user-attachments/assets/aa91832b-f604-4d9b-8e98-ad627dab8ffe" />

###  Click the realTime Button On
<img width="525" height="53" alt="스크린샷 2025-07-10 오후 9 08 10" src="https://github.com/user-attachments/assets/b9c7e290-0b09-493c-80c6-ba67cba97516" />



##  1. Send Message to Supabase Message Editor
 ```typescript
 export async function sendMessage({
        message,
        chatUserId
    }) {
          const supabase = await createServerSupabaseClient();
            const { data: { user }, error, } = await supabase.auth.getUser();

            if (error) {
                console.error(error)
                throw new Error("user is not authenticated");
            }

            const {data, error : sendMessageError} = await supabase.from("message").insert({
                message,
                receiver : chatUserId,
                sender : user.id, 
            })

            if(sendMessageError) {
                throw new Error(sendMessageError.message);

                
            }

            return data;

    }




      const sendMessageMutation = useMutation({
      mutationFn: async() => {
        return sendMessage({
          message,
          chatUserId : selectedIndex,
        })
      },
      onSuccess: () => {
        setMessage("");
        getAllMessage.refetch();
      }

    })




    <Input value={message} onChange={(e)=>{setMessage(e.target.value)}} placeholder="메세지를 입력하세요" type="text" /> 
    <Button  onClick={()=>{sendMessageMutation.mutate()}} className="min-w-20" color="light-blue" >전송</Button>

```


##  2. Get Message From Supabase Message Editor


 ```typescript


export default function Message({
    isFromMe,
    message,
}) {
  return (
  
        <p>
            {message}
        </p>

   )
}




export async function getAllmessages({
    chatUserId
}) {
        const supabase = await createServerSupabaseClient();
        const { data: { user }, error, } = await supabase.auth.getUser();

            if (error) {
                console.error(error)
                throw new Error("user is not authenticated");
            }

            const {data , error : getMessageError} = await supabase
            .from("message")
            .select("*")
            .or(`receiver.eq.${chatUserId},receiver.eq.${user.id}`)
            .or(`sender.eq.${chatUserId},sender.eq.${user.id}`)
            .order("created_at",{ascending:true});

            if (getMessageError) {
                return []
            } 

            return data;

 
}





   const getAllMessage = useQuery({
      queryKey: ["messages",selectedIndex],
      queryFn: () => getAllmessages({chatUserId : selectedIndex}),
     enabled: !!selectedIndex,
      

    })




   {getAllMessage.data?.map((message)=>(
      <Message key={message.id} message={message.message} isFromMe={message.receiver === selectedIndex} />
     ))} 

```

##  3. SubScribe 

⚡️ If you subscribe your database table and then change data of your table for example insert  , or update then code will notice you 

  ```typescript
   const  waitingChannel = supabase.channel('waiting_users_changes')
    .on('postgres_changes', {
      event: 'INSERT',
      schema: 'public',
      table: 'waiting_users'
    }, async payload => {
        // when table will be changed and then you get the notice 
    }
```

