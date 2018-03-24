# DataAuthorisation

we have Client and ServiceProvider

`Client` require some services from the `service provider`. so that client requires to send some data to the service provider.

Ex. Paytm

 
`Problem: How would service provider will ensure that its data is not tempered or its not altered during network call.`

Solution: 

The `client` would send a unique key and confidential key to the `client`.  
say:- "hello#@"



`Client` would also send one more thing ie `client` unique id.  
say:- "1205"


now what `client` will do is.
suppose he has following data:


```
Name					
Address				 
Amount				
Transaction Id		
Success URL			
Failure URL			
```

so now with any hashing technique which that `service provider` use will or the hashing technique suggested by `service provider` , `client' will encrypt its data and will send it to the `service provider`.

Ex.


```
Name	: Piyush				
Address: India				 
Amount: 250 INR				
Transaction Id: 98569923245		+  unique and confidential key (private key ie hello#@) + (encrypt) = mpyu#@ay?((
Success URL: www.success.transaction.com			
Failure URL: www.failure.transaction.com			
```

`mpyu#@ay?((` this is the encrypted key created by `client`.

now `client` will send the data with this encrypted key to the `service provider`.

now `client` will send-

```
Name	: Piyush				
Address: India				 
Amount: 250 INR				
Transaction Id: 98569923245									this data will be send to the service provider
Success URL: www.success.transaction.com			
Failure URL: www.failure.transaction.com	
Client key: 1205	
Encrypted Id: mpyu#@ay?((	
```

note: here client is sending `1205`, so that service provider will come to know that this request is coming from which `client` and `service provider` will have corresponding secret key for that `client` and `client` will again create one encryted key and will match that key again with `client's` shared key both should be same. ie `service provider` will again get the same encrypted id as `mpyu#@ay?((`


----

now below is the process service provider will follow:

service provider will get following data -

```
Name	: Piyush				
Address: India				 
Amount: 250 INR				
Transaction Id: 98569923245									
Success URL: www.success.transaction.com			
Failure URL: www.failure.transaction.com	
Client key: 1205	
Encrypted Id: mpyu#@ay?((	
```

now client will have corresponding key with client `1205` 
say it is `hello#@`

now `service provider` will again encrypt the data and will generate Encrypted Id.

```
Name	: Piyush				
Address: India				 
Amount: 250 INR				
Transaction Id: 98569923245		+  unique and confidential key (private key ie hello#@) + (encrypt) = mpyu#@ay?((
Success URL: www.success.transaction.com			
Failure URL: www.failure.transaction.com			
```
here `service provider` is getting `mpyu#@ay?((` as key which is similar to the key sent by client hence data is not tampered.

say data is tempered or changed, then encrypted key would be different.

```
Name	: Sameer 				
Address: India				 
Amount: 250 INR				
Transaction Id: 98569923245		+  unique and confidential key (private key ie hello#@) + (encrypt) = oiu8.as8*//
Success URL: www.success.transaction.com			
Failure URL: www.failure.transaction.com			
```


`oiu8.as8*//` is not equals with encrypted key `mpyu#@ay?((` sent by client.

hence here data is tempered.
