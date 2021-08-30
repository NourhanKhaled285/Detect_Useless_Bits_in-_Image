function [B] = DetectUselessBitsInImage(I)

%UNTITLED Summary of this function goes here
%   Detailed explanation goes here



img1=imread(I);


grayim=rgb2gray(img1);

[H,W,L]=size(grayim);





c=1;



sum=[0,0,0,0,0,0,0,0];



list=[];

 
try
  
  for i =1:H
    
     for j=1:W
    
    x=grayim(i,j);
    
    xbin=dec2bin(x);
      
  strl=strlength(xbin);
        
    
    if strl==0
           
 sum=sum+1;
       
 else
            
       if strl<8
           for v=1:(8-strl)
             xbin=append('0',xbin);  
             
           end
       end  
          
     
           
           
         for bitno=1:8
            if xbin(bitno)=='1'
                
                sum(bitno)=sum(bitno)+1;
                
                 
            end
            
            
       
         end
         
       
       
      
        end
        
    end
    
end 
 catch ME
     x;
     
   xbin;
 end
  
 


 for indexv =1:8
     if sum(indexv)<(0.1*(H*W))
         list(c)=indexv;
         c=c+1;
     end
 end
 B=list
 

end