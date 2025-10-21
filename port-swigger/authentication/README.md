LAB 11:
  i had to get carlos acc and delete it by getting his password from the stay-login cookie ,
  how did we get this cookie in the first place? well there was an xss vulnerability in the comments so i wrote the java script that says
  "got to this website and get the specific documents " this way my  exploit web will give me the staylogin cookie that i decoded in burp than
  cracked the hash in crackstation.com and i got the pass since these cookies have the users pass in it .

LAB 12: 
  i had to brute force the username and the password, the username is guessed by the response time ,
  in burp in repeater they show us the time ms or mill, so when the usrname is correct the system checks the pass wich takes much time than when the username 
  is wrong cuasse it wont check the pass , this way by making the pass so big that when the usrername is right you will know
  , plus it blocks your ip afrter few attempts so you have to change the X-Forwarded-For: ip
