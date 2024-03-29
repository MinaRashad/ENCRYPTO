# ENCRYPTO
a Simple JavaScript Library To help crypting easly. 

It contains Cyphers like: reverse, Caeser, transposition,
                          monoAlphabetic. atbash , affine
                          simpleShiftVigenere, autoKeyVigenere
                          
It Also contains some hashes like:
                          32bit Integer hash code, SHA1 hash
The Library Also contains: BruteForce That will work for Any hash or any cypher that take one value like 'atbash'
                            Caeser Cracker More Crackers are coming soon
# How To Use ...


## Reverse:
  reverse(String): will return the string reversed
 
 Example:
              
              reverse('hello') => 'olleh'
              reverse('olleh') => 'hello'
 
 
## Caeser:
  caeser(String, Key, isEncrypt [Optional] ): isEncrypt default value is true if false it will decrypt instead
                                 
  Caeser encryption will take the string and shift every character by the key
  
**NOTE:** Caeser Will Return the Encryption All Capital letters
 
 Example: 
    
              caeser('Moon', 2) => 'OQQP'
              caeser('OQQP', 2, false) = 'MOON'
              
              
## Transposition:
   transposition(String, Key, isEncrypt [Optional] ): isEncrypt default value is true if false it will decrypt instead

   Based on a Special Algorithm , Transposition will change Places of All String Characters depending on the key
   
   **Highly recommended that When Transposition is used to use a key near to the half on the String**
   
   You can see more about it <a target='_blank' href='https://en.wikipedia.org/wiki/Transposition_cipher'>here</a>
   Examples:
   
              transposition('This is a Secret', 7) => 'T ehati sS eicsr'
              transposition('T ehati sS eicsr', 7, false) => 'This is a Secret'
              
## monoAlphabetic:
  monoAlphabetic(msg,keyPhrase,isEncrypt [optional] ) : isEncrypt default value is true if false it will decrypt instead
  
  MonoAlphabetic Takes a Secert phrase instead of a number Here are some Examples:
  
         monoAlphabetic('HelloWorld','secrt') => 'DTIILWLOIR'
         monoAlphabetic('DTIILWLOIR','secrt' , false) =>  'HELLOWORLD'
**NOTE: MAKE SURE THE KEY PHRASE DOES NOT HAS A REPEATING CHARACHTER. e.g. 'secret' will not work because there are 2 'e's**        
      
## atbash:
  atbash(msg,isEncrypt [optional]) : isEncrypt default value is true if false it will decrypt instead
  
  atbash will take each charachter and map it to the charachters in reverse
  
          atbash('Hello World') => "SVOOL DLIOW"
          atbash('SVOOL DLIOW', false) => 'HELLO WORLD'
          
## simple-Shift-Vigenere:
  simpleShiftVigenere(msg,keys,isEncrypt [optional]) : isEncrypt default value is true if false it will decrypt instead
  
  simpleShiftVigenere is a more safier version of caeser , It takes more than one key, then shifts each character with it after keys run out it reuses them.
  
          simpleShiftVigenere('hello World' , [5,11,0,0,13]) => 'MPLLB HORYI'
          simpleShiftVigenere('MPLLB HORYI' , [5,11,0,0,13],false) => 'HELLO WORLD'

## auto-Key-Vigenere:
  autoKeyVigenere(msg, keys, isEncrypt [optional]) : isEncrypt default value is true if false it will decrypt instead
  
  auto-Key-Vigenere is the one of the safest cyphers . autoKeyVigenere , like simpleShift , Take more than one key but instead of repeating Keys, It uses the Original message as a key. 
  **Then It return it as some blocks of length of 4 as an extra layar of security which means decrypted text can be unreadable if you do not know what to look for**
  
          autoKeyVigenere('Super Secret Message',[12,4,0,16]) => ' EYPU JMTG IWXO VWLM KW'
          autoKeyVigenere( 'EYPU JMTG IWXO VWLM KW',[12,4,0,16],false) => 'SUPE RSEC RETM ESSA GE'
          

# Hashes:
## 32bit Integer:
   This is a hash which means It can not be decrypted by an Algorithm
  
  'YourText'.hashCode() will return a 32bit integer
   
   Example:
               
               'Hello'.hashCode() => 69609650
               'hello'.hashCode() => 99162322
               
## SHA1:
  Also a Very Famous hash **SHA1 Code is not mine**
  Read about it <a target='_blank' href='https://en.wikipedia.org/wiki/SHA-1'>here</a>
  Example:
              
              SHA1('Super Imporant Text') => '000a7b9aeba75024c4d02b1e61d098867857459a'
              
              
# Cracking:
  this part is used to crack more will be add later
  
## Caeser-Cracker
   caeserCracker(target,key = 1,baseArr=[]) the target is the encrypted text, this will show all possible using a bruteforce method using all possible 27 keys
   
   **DO NOT CHANGE EITHER THE key NOR baseArr to work as expected**
   
   Example:
    
           caeserCracker('OQQP') =>
   
            [
            "PRRQ", "QSSR", "RTTS", "SUUT", "TVVU",
            "UWWV", "VXXW", "WYYX", "XZZY", "YAAZ",
            "ZBBA", "ACCB", "BDDC", "CEED", "DFFE",
            "EGGF", "FHHG", "GIIH", "HJJI", "IKKJ",
            "JLLK", "KMML", "LNNM", "MOON", "NPPO", "OQQP"
            ]                        ^^^^
                                this is the decrypted text
                                
# BruteForce
  **This function can only hack functions that take one required argument e.g. SHA1(msg), atbash(msg, isEncrypt [optional])**
  The function will try to Encrypt(or hash) every possible combination until the target is equal to the encrypted combination
##  How to use

  bruteForce(method,target,testSmall=true,testCapital=false,testSpecialCharacters=false,testNum = false,len=1)
  
  **method**: you will put the function which was used to encrypt/hash, in this example we will use SHA1
  
  **target**: you will put the encrypted text , in the example we will use this hash "9d989e8d27dc9e0ec3389fc855f142c3d40f0c50"
  
  **Testsmall**: if you want it to test small charachters , by default it will check small letters only except if you change the following
  
  **testCapital**: if you want it to check capital letters
  
  **testSpecialCharachters**: like {* ,& ,^ ,% , ..etc }
  
  **testNum**: will check numbers
  
  **len**: this is the starting length change it if you want to start from a bigger
  
  **NOTE** the more test elements you make true the slower it will come
  
  Examples:
  
          bruteForce(SHA1,'9d989e8d27dc9e0ec3389fc855f142c3d40f0c50') => 'cat'
          bruteForce(SHA1,"2bdb2e4ca4081ac3953f358521ff3396fa06ee4a",false,false,true,true) =>'1+1=2'
          
   **WARNING: MAKE SURE NOT TRY CRACK MORE THAN YOUR COMPUTER LIMITS For Example, Second Example TAKES LOTS OF TIME TO CHECK Especially when it is continuelly hashing the combination with SHA1**
   
   A more advanced Example to Check for 32bit number hash, An Example of how to use a function made in the arguments
   
          bruteForce((str)=>{return str.hashCode()}, 3351631) => 'mina'
   
   
