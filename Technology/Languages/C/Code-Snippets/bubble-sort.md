```C
BubbleSort()
{
	 int r,t;
     int i,u,y;
     i=u=y=0;
     int arr[10];
     for (i=0;i<10;i++){
         arr[i]=rand()%101;
         printf(" %d \t",arr[i]);
     }

     printf("\n");
     i=0;
     for (u=0;u<10;u++){
         for (i=0;i<9-u;i++){
             if (arr[i]<arr[i+1]){
                 t=arr[i];
                 arr[i]=arr[i+1];
                 arr[i+1]=t;
                 }
         } 

     for (i=0;i<10;i++){
     printf(" %d \t",arr[i]);
     } 
```
