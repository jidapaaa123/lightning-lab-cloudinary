Source: https://www.youtube.com/watch?v=LzMXdnABrCM  

1) Clone the repo  
2) Run [ npm install ]  
3) Go to cloudinary.com  
    a) Go to Home  
    b) Under “Product Environment” section, click “Go to API Keys”  
4) Make an .env file in your root folder:  
```  
CLOUDNAME=public
CLOUDAPIKEY=public
CLOUDINARYSECRET=KEEPTHISPRIVATE
```  
5) Replace those lines with your actual info from Cloudinary  
6) Go to public > client-side.js  
    a) update api_key and cloud_name there as well  
7) Run with [ npm run dev ]  
8) Go to localhost:3000  
    a) username: admin  
    b) password: admin  

**Relevant Parts of the code:**  
* data.txt: the website is set up to store public ID values of the images there. Those ID’s are used to create URL’s that can access the images stored in the Cloudinary server  
* Per file upload, create a signature. This verifies that it’s valid, since the signature includes the API_Secret  
    * server.js: /get-signature  
    * client-js: Uploading to Cloudinary, will have the public_id of the image returned back as part of the response  
    * server.js: /do-something-with-photo verifies that the response received, is really from Cloudinary via cross-checking if the signature is in line with the API_Secret  
* Interacting with the photos: server.js: /view-photos, /delete-photo  