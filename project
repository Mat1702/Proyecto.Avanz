#include<iostream>
#include <string.h>
#include<fstream>
#include <stdio.h>
#include <locale.h>
#include <iomanip>


using namespace std;

struct registro
{
    char nombre[20];
    char apellido[20];
    int edad;
    int id;
    char orige[20];
    char destino[20];
};

registro pasa_aux;
registro cargar_pasa();
int cant;
void ver();
void buscar();
void modificar();
void eliminar();
void agregar();

int main(){
    int menu;
     cout<<endl;
        cout<<"Va a crear una base de datos en binario llamada pasajero.dat: "<<endl;
        cout<<"ok? PRESIONE ENTER"<<endl;
        FILE* archi = fopen("pasajero.dat", "wb");

        char resp='s';

        while(resp!='n'){
        pasa_aux=cargar_pasa();

        fwrite( &pasa_aux, sizeof(registro), 1, archi );
         cout<<endl;
        cout << "Desea reservar mas pasajero ( s/n ): ";

        cin>>resp;

        }
        fclose(archi);
        cout<<endl;

      do{
        cout<<"\t\tUsuario porfavor escoja una de las siguientes opciones: "<<endl;
        cout<<endl;
        cout<<"1. visualizar los pasajeros en la base de datos"<<endl;
        cout<<"2. agregar pasajeros en la base de datos "<<endl;
        cout<<"3. buscar pasajeros en la base de datos"<<endl;
        cout<<"4. eliminar pasajeros en la base de datos "<<endl;
        cout<<"5. modificar pasajeros en la base de datos"<<endl;
        cout<<"6. terminar programa"<<endl;
        cout<<"Ingrese su opcion: "<<endl;
            cin>>menu;
            switch (menu)
            {
                case 1:
                ver();
                break;
                case 2:
                agregar();
                break;
                case 3:
                buscar();
                break;
                case 4:
                eliminar();
                break;
                case 5:
                modificar();
                break;
                default:
                break;
            }
      }while(menu <=5);

    return 0;
}

registro cargar_pasa(){

  registro pasa_dian;
  string nombre,apelli,destino,orige;


          cin.ignore();
          cout<<"nombre: "<<endl;
          getline(cin, nombre);
          strcpy( pasa_dian.nombre, nombre.c_str());
          //cin.ignore();
          cout<<"apellido: "<<endl;
          getline(cin, apelli);
          strcpy( pasa_dian.apellido, apelli.c_str());
          cout<<"edad: (ENTERO)"<<endl;
          cin>>pasa_dian.edad;
          cin.ignore();
          cout<<"ID: (ENTERO)"<<endl;
          cin>>pasa_dian.id;
          cin.ignore();
          cout<<"Origen: "<<endl;
          getline(cin, orige);
          strcpy( pasa_dian.orige, orige.c_str());
          cout<<"Destino: "<<endl;
          getline(cin, destino);
          strcpy( pasa_dian.destino, destino.c_str());

    return pasa_dian;
}

void ver(){

ifstream archi;

archi.open("pasajero.dat",ios::binary | ios::in);
 cout<<endl;
archi.seekg(0);
registro pasa;
 archi.read( (char *)(&pasa), sizeof(registro) );
cout<<"nombre\tapellido\tedad\tID\t\tOrigen\tDestino"<<endl;
cout<<"___________________________________________"<<endl;
while(!archi.eof()){
   cout<<pasa.nombre<<setw(10)<<pasa.apellido<<setw(14)<<pasa.edad<<setw(10)<<pasa.id<<setw(10)<<pasa.orige<<setw(17)<<pasa.destino<<endl;
   archi.read( (char *)(&pasa), sizeof(registro) );

}
    archi.close();
}



void agregar()
{

    ofstream archi("pasajero.dat",ios::binary | ios::app);
     cout<<endl;
    cout<<"\t\tAgrege los datos de los pasajeros: "<<endl;
    char resp='s';

        while(resp!='n'){
        pasa_aux=cargar_pasa();

        archi.write( (char *)(&pasa_aux), sizeof(registro) );
        cout<<endl;
        cout << "Desea cargar mas pasajeros ( s/n ): ";

        cin>>resp;
        }
        archi.close();
        }


 void buscar(){

   ifstream archi;
char respues='s';

archi.open("pasajero.dat",ios::in);
int ids;
registro pasa;
int existe=0;

cout<<endl;
cout<<"Ingrese el id del pasajero a consultar: "<<endl;
cin>>ids;

while(!archi.eof()){
   archi.read( (char *)(&pasa), sizeof(registro) );
   if(ids==pasa.id){
   cout<<"nombre\tapellido\tedad\tID\t\tOrigen\tDestino"<<endl;
   cout<<pasa.nombre<<setw(10)<<pasa.apellido<<setw(14)<<pasa.edad<<setw(10)<<pasa.id<<setw(10)<<pasa.orige<<setw(17)<<pasa.destino<<endl;
   existe=1;

   }}
   if(existe==0){
       cout<<"No existe el estudiante"<<endl;
   }


    archi.close();
 }


 void eliminar(){
      fstream archilect("pasajero.dat");
      ofstream archiescr("auxiliar.dat");
   int ids;
   registro pasa;
   int existe=0;
   cout<<"\tIngrese el id del pasajero que desea eliminar: "<<endl;
   cin>>ids;
    while(!archilect.eof()){
   archilect.read( (char *)(&pasa), sizeof(registro) );


   while(archilect && !archilect.eof()){
    if(ids==pasa.id){
        cout<<"DATOS DEL ESTUDIANTE:"<<endl;
   cout<<"nombre\tapellido\tedad\tID\t\tOrigen\tDestino"<<endl;
   cout<<"___________________________________________"<<endl;
   cout<<pasa.nombre<<setw(10)<<pasa.apellido<<setw(14)<<pasa.edad<<setw(10)<<pasa.id<<setw(10)<<pasa.orige<<setw(17)<<pasa.destino<<endl;
   cout<<"\t\t**PASAJERO ELIMINADO**"<<endl;
   existe=1;
    }else{
    archiescr.write((char *)(&pasa), sizeof(registro));
    }
    archilect.read((char *)(&pasa), sizeof(registro));}

   archilect.close();
   archiescr.close();
   remove("pasajero.dat");
   rename("auxiliar.dat","pasajero.dat");
   }

   if(existe==0){
       cout<<"No existe el estudiante"<<endl;
   }}

void modificar(){
      fstream archilectura("pasajero.dat");
      ofstream archiescritura("auxiliares.dat");
   int ids,edad1,ids1;
   string nombre,origenes,destinos,appell;
   registro pasa;
   int existe=0;
   cout<<endl;
   cout<<"\tIngrese el id del pasajero que desea modificar: "<<endl;
   cin>>ids;
    while(!archilectura.eof()){
   archilectura.read( (char *)(&pasa), sizeof(registro) );


   while(archilectura && !archilectura.eof()){
    if(ids==pasa.id){
        cout<<"DATOS DEL PASAJERO:"<<endl;
   cout<<"nombre\tapellido\tedad\tID\t\tOrigen\tDestino"<<endl;
   cout<<"___________________________________________"<<endl;
   cout<<pasa.nombre<<setw(10)<<pasa.apellido<<setw(14)<<pasa.edad<<setw(10)<<pasa.id<<setw(10)<<pasa.orige<<setw(17)<<pasa.destino<<endl;
   existe=1;

   cout<<"Digite nuevo nombre o f para dejar el actual: "<<endl;
    cin.ignore();
     getline(cin,nombre);
     if(nombre=="f"){
         pasa.nombre;
     }else{
     strcpy(pasa.nombre,nombre.c_str());}

     cout<<"Digite nuevo apellido o f para dejar el actual: "<<endl;
     getline(cin,appell);
      if(appell=="f"){
         pasa.apellido;
     }else{
     strcpy(pasa.apellido,appell.c_str());}
     cout<<"Digite nueva edad o 0 para dejar el actual: "<<endl;
    cin>>edad1;
    if(edad1==0){
        pasa.edad;
    }else{
        pasa.edad=edad1;
    } cout<<"Digite nueva id o 0 para dejar el actual: "<<endl;
    cin>>ids1;
    if(ids1==0){
        pasa.id;
    }else{
        pasa.id=ids1;
    } cout<<"Digite nuevo origen o f para dejar el actual: "<<endl;
    cin.ignore();
     getline(cin,origenes);
      if(origenes=="f"){
         pasa.orige;
     }else{
     strcpy(pasa.orige,origenes.c_str());}
    cout<<"Digite nuevo destino o f para dejar el actual: "<<endl;
     getline(cin,destinos);
      if(destinos=="f"){
         pasa.destino;
     }else{
     strcpy(pasa.destino,destinos.c_str());}


    archiescritura.write((char *)(&pasa), sizeof(registro));
    }else{
    archiescritura.write((char *)(&pasa), sizeof(registro));
    }
    archilectura.read((char *)(&pasa), sizeof(registro));}

   archilectura.close();
   archiescritura.close();
   remove("pasajero.dat");
   rename("auxiliares.dat","pasajero.dat");
   }

   if(existe==0){
       cout<<"No existe el pasajero"<<endl;
   }}
