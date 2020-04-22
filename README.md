# DFS
#include <stdio.h>
#include <conio.h>
#include <iostream>
#define MAX 50
#define TRUE 1
#define FALSE 0
int A[MAX][MAX], n,chuaxet[MAX];
void Init(void){
  int i,j;FILE *fp;
  fp=fopen("DOTHI.IN","r");
  fscanf(fp,"%d",&n);
  printf("\n So dinh do thi:%d",n);
  for(i=1; i<=n; i++){
    printf("\n");chuaxet[i]=TRUE;
    for(j=1; j<=n; j++){
      fscanf(fp,"%d",&A[i][j]);
      printf("%3d",A[i][j]);
    }
  }
}
void DFS_Dequi(int u){
  int v;
  printf("%3d",u);chuaxet[u]=FALSE;
  for(v=1; v<=n; v++){
    if(A[u][v] && chuaxet[v])
      DFS_Dequi(v);
  }
}
void DFS_Stack(int u){
  int Stack[MAX], dau=1, s, t;
  Stack[dau]=u;chuaxet[u]=FALSE;
  printf("%3d",u);
  while(dau>0){
    s=Stack[dau];dau--; //pop s out the stack
    for(t =1;t<=n; t++){
      if(chuaxet[t] && A[s][t]){
        printf("%3d",t);
        chuaxet[t] = FALSE;
        Stack[++dau]=s; //push s into the stack
        Stack[++dau]=t;break; //push t into the stack
      }
    }
  }
}
int main(void){
  int u ;
  Init();
  std::cout<<"\n Dinh bat dau duyet: ";
  std::cin>>u;
  DFS_Stack(u);
  //DFS_Dequi(u);
  getch();
  }
