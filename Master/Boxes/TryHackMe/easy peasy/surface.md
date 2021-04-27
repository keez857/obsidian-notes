    viewing source on /hidden/whatever gets us this:  
  
ZmxhZ3tmMXJzN19mbDRnfQ==  
  
decoding thru base64:  
  
**flag{f1rs7\_fl4g}**  
  
  
  
  
**visiting 10.10.124.156:65524 reveals the third flag**  
  
  
  
[http://10.10.124.156:65524/robots.txt](http://10.10.124.156:65524/robots.txt) reveals clue about user-agent  
  
a18672860d0510e5ab6699730763b250 is an md5 hash that you can only crack on this website:  
[https://md5hashing.net/hash](https://md5hashing.net/hash)  
  
  
  
  
Running the 3rd flag through crackstation: 9fdafbd64c47471a8f54cd3fc64cd312  
Result: **candeger**  
  
  
  
viewing source of 10.10.124.156:65524  
  
finds this: <p hidden>its encoded with ba....:ObsJmP173N2X6dOrAgEAL0Vu</p>  
  
Base62 decoding this reveals hidden directory **/n0th1ng3ls3m4tt3r**  
  
  
Going the the hidden directory reveals this text: 940d71e8655ac41efb5f8ab850668505b86dd64186a66e57d1483e7f5fe6fd81  
  
This is a GOST hash based on hint. Using john to decode with the wordlist easypeasy.txt  
Password: **mypasswordforthatjob**  
  
You can use this password the extract file from binarycodepixabay.jpg using steghide  
  
Looking at the text file extracted gives us credentials  
  
**user: boring  
password: iconvertedmypasswordtobinary**