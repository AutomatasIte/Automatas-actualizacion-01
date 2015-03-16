# Automatas-actualizacion-01
Automatas-actualizacion-01

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

typedef struct
{
char c[20];
int token;
}asig_tok;
asig_tok atoken[]={
{"/",0},{"/=",1},
{".",2},{"..",3},
{"&",4},{"&=",5},{"&&",6},
{"|",7},{"|=",8},{"||",9},
{"-",10},{"-=",11},{"--",12},
{"+",13},{"+=",14},{"++",15},
{"<",16},{"<=",17},{"<<",18},{"<<=",19},
{"<>",20},{"<>=",21},
{">",22},{">=",23},{">>=",24},{">>>=",25},{">>",26},{">>>",27},
{"!",28},{"!=",29},{"!<>",30},{"!<>=",31},{"!<",32},{"!<=",33},{"!>",34},{"!>=",35},
{"(",36},{")",37},
{"[",38},{"]",39},
{"{",40},{"}",41},
{"?",42},
{",",43},{";",44},
{":",45},
{"$",46},
{"=",47},{"==",48},
{"*",49},{"*=",50},
{"%",51},{"%=",52},
{"^",53},{"^=",54},{"^^",55},
{"~",56},{"~=",57},
{"@",58},
{"=>",59},
{"#",60},
{"abstract",61},{"alias",62},{"aling",63},{"asm",64},{"assert",65},{"auto",66},
{"body",67},{"bool",68},{"break",69},{"byte",70},
{"case",71},{"cast",72},{"catch",73},{"cdouble",74},{"cent",75},{"cfloat",76},{"char",77},{"class",78},{"const",79},{"continue",80},{"creal",81},
{"dchar",82},{"debug",83},{"default",84},{"delegate",85},{"delete",86},{"deprecated",87},{"do",88},{"double",89},
{"else",90},{"enum",91},{"extern",92},{"esport",93},
{"false",94},{"final",95},{"finally",96},{"float",97},{"for",98},{"foreach",99},{"foreach_reverse",100},{"function",101},
{"goto",102},
{"if",103},{"ifloat",104},{"immutable",105},{"import",106},{"in",107},{"inout",108},{"int",109},{"interface",110},{"ireal",111},{"is",112},
{"long",113},
{"mixin",114},{"module",115},
{"new",116},{"null",117},
{"override",118},
{"package",119},{"pagmas",120},{"private",121},{"protected",122},{"public",123},{"pure",124},
{"real",125},{"ref",126},{"return",127},
{"shared",128},{"short",129},{"static if",130},{"struct",131},{"super",132},{"switch",133},
{"template",134},{"this",135},{"trow",136},{"true",137},{"try",138},{"typedef",139},{"typeid",140},{"typeof",141},
{"ubyte",142},{"ucent",143},{"uint",144},{"ulong",145},{"union",146},{"unittest",147},{"ushort",148},
{"version",149},{"void",150},
{"wchar",151},{"while",152},{"with",153},{"writeln",154},
{"Palabra Reservada",155},{"stdio",156},{"main",157},{"\"",158},{" ",159},{"\"",160},{"numero",1000}
};

    struct node
    {
     char info[30];
     int linea;
     int ntoken;
     struct node *sig;
    };
    typedef struct node nodo;
    typedef nodo *tipolista;
    tipolista lista=NULL;


  void crear(tipolista *lista,char x[30],int p,int u)
  {
     tipolista j, uri=*lista;
     j=(nodo*)malloc(sizeof(nodo));
     strcpy(j->info,x);
     j->linea=p;
     j->ntoken=u;
     j->sig=NULL;
     
     if(*lista==NULL)
     *lista=j;
     
     else
     { while(uri->sig!=NULL)
       uri=uri->sig;
       uri->sig=j;
     }
  }
  
  
  

   int parea(int n)
   {
       if(n==lista->ntoken)
       {
       printf("%s ok \n",lista->info);
       lista=lista->sig;
       return 1;
       }
      
       else
       {
        printf("%s error \n",lista->info);
        return 0;
       }
   }
   
   
   
   


   void automata()
   {
    int a;
    
      while(lista!=NULL)
      {
        switch(lista->ntoken)
        {
            case 109:
                     printf("%s ok \n",lista->info);
                     lista=lista->sig;
                     a=parea(155);
                     a=parea(44);
                     break;
                     
            case 154:
                 printf("%s ok \n",lista->info);
                     lista=lista->sig;
                     a=parea(36);
                     a=parea(160);
                     a=parea(155);
                     a=parea(160);
                     a=parea(37);
                     a=parea(44);
                     break;
                     
        ////    case 103: PENDIENTE
                 
                //// funcion_if();
                    
        }

        ///lista=lista->sig; 
            
      }

   }




       void imprimir(tipolista *p)
       {
         tipolista u;
         u=*p;
         
           while(u!=NULL)
           {
            printf("%s, %d ,%d \n",u->info,u->linea,u->ntoken);
            u=u->sig;
           }
       }
       
       

       int main()
       {//////////////inicio
         printf("\n PROGRAMA QUE ABRE UN ARCHIVO DE TEXTO \n");

         FILE* miarchivo=NULL;
         char* nombrearchivo="hola5.txt";
         char fila;
         char cadena[50];
         int u=0;
         int linea=0;
         int i,z,uri=0;
         miarchivo=fopen(nombrearchivo,"r");

         while(feof(miarchivo)==0){ ////INICIO DEL WHILE
         fila=fgetc(miarchivo);
         uri=0;


         if(fila!='\n')
         {
             if(fila!=' ')
             {
              cadena[u]=fila;
              u++;
             }
         }


         if((fila==' ')||(fila=='\n'))
         {   /////////////uno inicio
           cadena[u]='\0';
           for(i=0;i<162;i++)
           {
            if(strcmp(cadena,atoken[i].c)==0)
           {
           z=atoken[i].token;
           uri=1;
           }
         }

         if(uri==0)
         {
          z=155; /////// con 155 me refiero a que es una palabra normal
         }

         crear(&lista,cadena,linea,z);
         u=0;
         free(cadena);
         }

         if(fila=='\n')
         linea++;

         }

          fclose(miarchivo);
          /////
          ///imprimir(&lista);
          automata();
          system("PAUSE");
          return 0;
         }/////////fin



