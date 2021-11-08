# Mailchimp-Integration-Documentation

Mailchimp Integration Documentation


1-	Log-in to your account.
2-	Go to your account 
3-	Click on extra
4-	API Key.




![image](https://user-images.githubusercontent.com/51037193/140786653-23f2a281-4b25-4841-abc5-518e54d318d7.png)





If you don’t have a key, create a key.

 
![image](https://user-images.githubusercontent.com/51037193/140786718-e7681395-4073-4dd6-a96e-255cda42a56e.png)


Then you must click on the link below to know how to use the create, Read, Edit, and Delete.  
https://mailchimp.com/developer/marketing/api/lists/ 








Here the path parameter you will used it on the list.
https://mailchimp.com/developer/marketing/api/lists/batch-subscribe-or-unsubscribe/ 
all you need a list ID and you can provide the members that you want to subscribe in the body of request 
 

![image](https://user-images.githubusercontent.com/51037193/140786750-c3ff03c6-d3d8-4a19-a9a0-257f700522ce.png)











Let’s get our list ID.
1-	Go to Audience


![image](https://user-images.githubusercontent.com/51037193/140786769-8edcd572-f37a-4199-a703-48a13ffd232b.png)











2-	Then manage audience.
3-	Settings.

 
![image](https://user-images.githubusercontent.com/51037193/140786781-c7164705-f6ac-491f-993b-41156bb5856c.png)


4-	Unique ID for audience. (This is a list ID for your list)

 ![image](https://user-images.githubusercontent.com/51037193/140786806-be1ede16-c149-4f8a-940c-4480d3205a07.png)





























Then you must check the members Properties by click on “show properties”

 
![image](https://user-images.githubusercontent.com/51037193/140786823-3003a541-238b-418e-a1e5-d643a53fcec0.png)




We need to use the email_address, status, and merge_fields.
This is javascript code.


![image](https://user-images.githubusercontent.com/51037193/140787310-655224b8-f2c4-4471-8813-8eb715a11dae.png)




app.post("/" , function(req , res){

    const firstName = req.body.Fname
    const lastname = req.body.Lname
    const email = req.body.email

    const data = {
        members:[
            {
                email_address: email,
                status: "subscribed",
                merge_fields:{
                    FNAME: firstName,
                    LNAME: lastname
                }
            }
        ]
    };


If you want to check the marge fields 
1-	Audience.
2-	Settings.
3-	Audience fields and *|Merge|* tag
![image](https://user-images.githubusercontent.com/51037193/140786924-6344e2dd-d822-4c67-81f9-8258a563afd9.png)

















Now we have our data object completed, but this is Javascript and what we need is actually to turn this into a flatpack Json.

    const data = {
        members:[
            {
                email_address: email,
                status: "subscribed",
                merge_fields:{
                    FNAME: firstName,
                    LNAME: lastname
                }
            }
        ]

So, I’m going to create a new variable called jsonData and I’m going to send this to JSON.stringify(data) and I’m going to pass in my data into here so that I turn this data into a string that is in the format of a JSON. 

    const jsonData = JSON.stringify(data);



And I’m going to set the url
                                                          List_id
   const url = "https://us5.api.mailchimp.com/3.0/lists/1f6ef0d526";

list_id = 1f6ef0d526


and in the url here we have  https://us5.api.mailchimp.com/ the us5 that in the beginning of the url 
You must replace the number 5 with the number that you have in your API key after the word us
// API Key
// 4cd5fb044rf76f774593aac71b61308a-us5

Mailchimp has several servers that they’re running simultaneously because they’re a big operation. 
And when you are sign-up, you get randomly assigned to one of them and it could be anywhere from U.S. 1 – 20
NOTE: take a look at your API key and see what number you’ve got after the word us and copy that number and replace it with the number in the url.
