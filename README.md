# Clientes_api
Ejercicio de micro servicios usando ApiRESTful 
los end point son
/api/vi/clientes  #llama a todos los datos de los clientes en json -->para buscar se utuliza una peticion http "get"
/api/v1/cliente   #es para crear un cliente nuevo -->para buscar se utuliza una peticion http "post"
/api/v1/cliente/{id} #actualiza un cliente con un id unico -->para buscar se utuliza una peticion http "put"
/api/vi/cliente_dele/{id} #borra un cliente de cuerdo con su id unico -->utiliza una peticion http "delete"
/api/vi/cliente/{id} #busca un cliente de acuerdo al id unico y muestra los datos del mismo  -->para buscar se utuliza una peticion http "get"


esta api usa 4 microservicios 

- un servicio de configuracon global
   - donde se encuentran las configuraciones de los servicio utilizados para encapsular la mayoria de configuracion utilizado por la api
   - este micro servicio esta configurado para no ser visible en spring cloud para una capa de seguridad

- un servcio eureka
   - para registrar y ver los microservicios de spring cloud dados de alta

- un servicio gateway
   - para distribuir las peticiones a cada servicio correspondiente y evitar la comunicacion directa con el servicio

- un servicio de cliente
   - este servicio hace las operaciones crud en mysql el cual tiene varias capas divididas para evitar la confucion
   - controller es dodne se ecuentran los puntos de acceso
   - dto es el paquete para visualizar datos obtenidos de la base de datos
   - entites es el pquete que principal que se cominunica con la bd
   - http->responce es para las respuestas obtenidas por las peticiones http visualidas en json
   - service es la capa de servicio general que hace la mayoria de la logica de las opeciones crud
