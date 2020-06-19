# utl-keeping-leading-and-trailing-zeros-in-character-fields-with-ods-excel-output
keeping leading and trailing zeros in character fields with ods excel output 
    keeping leading and trailing zeros in character fields with ods excel output                                                        
                                                                                                                                        
        The best solution is to preprocess and put a tab in front of the number?                                                        
                                                                                                                                        
        Four techinques were tried                                                                                                      
                                                                                                                                        
                  a.  valzTagAtr  style(column)=[tagattr="type:text"];                                                                  
                  b.  valzBacTic  `00.100 fails (bactic is present)                                                                     
                  c.  valzEqlTab  =09x00.100 equal and tab in front fails leading and trailing 0s gone                                  
                                                                                                                                        
                ++d.  valzTab     THIS IS THE ONLY ONE WITH PERSISTENT LEADING AND TRAILING 0s                                          
                                                                                                                                        
    github                                                                                                                              
    https://tinyurl.com/y9gvrwev                                                                                                        
    https://github.com/rogerjdeangelis/utl-keeping-leading-and-trailing-zeros-in-character-fields-with-ods-excel-output                 
                                                                                                                                        
    StackOverflow                                                                                                                       
    https://tinyurl.com/y8wnbglh                                                                                                        
    https://stackoverflow.com/questions/62342380/when-using-ods-excel-statement-stop-excel-converting-numbers-saved-as-character        
                                                                                                                                        
    *_                   _                                                                                                              
    (_)_ __  _ __  _   _| |_                                                                                                            
    | | '_ \| '_ \| | | | __|                                                                                                           
    | | | | | |_) | |_| | |_                                                                                                            
    |_|_| |_| .__/ \__,_|\__|                                                                                                           
            |_|                                                                                                                         
    ;                                                                                                                                   
                                                                                                                                        
    data leading_zeros;                                                                                                                 
      length                                                                                                                            
         valzTagAtr                                                                                                                     
         valzBacTic                                                                                                                     
         valzEqlTab                                                                                                                     
         valzTab   $10;                                                                                                                 
      do val=.1 to .3 by .1;                                                                                                            
         valzTagAtr =put(val,z6.3);                                                                                                     
         valzBacTic =cats('`',put(val,z6.3));                                                                                           
         valzEqlTab =cats('=','09'x,put(val,z6.3));                                                                                     
         valzTab    =cats('09'x,put(val,z6.3));                                                                                         
         drop val;                                                                                                                      
         output;                                                                                                                        
      end;                                                                                                                              
                                                                                                                                        
    run;quit;                                                                                                                           
                                                                                                                                        
      VALZTAGATR  VALZBACTIC  VALZEQLTAB  VALZTAB                                                                                       
                                                                                                                                        
      00.100      `00.100     =T00.100*   00.100                                                                                        
      00.200      `00.200     =T00.200    00.200                                                                                        
      00.300      `00.300     =T00.300    00.300                                                                                        
                                                                                                                                        
     * T is for '09'x tab                                                                                                               
                                                                                                                                        
    *            _               _                                                                                                      
      ___  _   _| |_ _ __  _   _| |_                                                                                                    
     / _ \| | | | __| '_ \| | | | __|                                                                                                   
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                    
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                   
                    |_|                                                                                                                 
    ;                                                                                                                                   
                                                                                                                                        
    AFTER GOING TO EACH CELL AND HITTING F2 then ENTER                                                                                  
                                                                                                                                        
                                       **BEST OPTION VALZTAB?                                                                           
                                       * preprocess and add tab character in front;                                                     
    ------------------------------------------------                                                                                    
    |VALZTAGATR  VALZBACTIC  VALZEQLTAB  VALZTAB   |                                                                                    
    |----------------------------------------------|                                                                                    
    | 0.1      | `00.100   |    0.1    |  00.100   |                                                                                    
    |----------+-----------+-----------+-----------|                                                                                    
    | 0.2      | `00.200   |    0.2    |  00.200   |                                                                                    
    |----------+-----------+-----------+-----------|                                                                                    
    | 0.3      | `00.300   |    0.3    |  00.300   |                                                                                    
    ------------------------------------------------                                                                                    
                                                                                                                                        
    *         _           _     ___   _        _          _                                                                             
    __      _| |__   __ _| |_  |_ _| | |_ _ __(_) ___  __| |                                                                            
    \ \ /\ / / '_ \ / _` | __|  | |  | __| '__| |/ _ \/ _` |                                                                            
     \ V  V /| | | | (_| | |_   | |  | |_| |  | |  __/ (_| |                                                                            
      \_/\_/ |_| |_|\__,_|\__| |___|  \__|_|  |_|\___|\__,_|                                                                            
                                                                                                                                        
    ;                                                                                                                                   
    %utlfkil(d:/xls/leading_zeros.xlsx);                                                                                                
                                                                                                                                        
    data leading_zeros;                                                                                                                 
      length                                                                                                                            
         valzTagAtr                                                                                                                     
         valzBacTic                                                                                                                     
         valzEqlTab                                                                                                                     
         valzTab   $10;                                                                                                                 
      do val=.1 to .3 by .1;                                                                                                            
                                                                                                                                        
         valzTagAtr =put(val,z6.3);                                                                                                     
         valzBacTic =cats('`',put(val,z6.3));                                                                                           
         valzEqlTab =cats('=','09'x,put(val,z6.3));                                                                                     
         valzTab    =cats('09'x,put(val,z6.3));                                                                                         
         drop val;                                                                                                                      
         output;                                                                                                                        
      end;                                                                                                                              
                                                                                                                                        
    run;quit;                                                                                                                           
                                                                                                                                        
    ods excel file="d:/xls/leading_zeros.xlsx";                                                                                         
    proc report data=leading_zeros nowd missing ;                                                                                       
    define valzTagAtr /  style(column)=[tagattr="type:text"];                                                                           
    run;quit;                                                                                                                           
    ods excel close;                                                                                                                    
                                                                                                                                        
                                                                                                                                        
