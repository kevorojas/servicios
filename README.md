Hola que tal amigos, en esta ocasion vamos a hablar sobre los servicios en Kubernetes.

Los servicios son un objeto aislado encargado de observar a los pods a traves de una etiqueta o label en especifico para luego poder acceder a ellos a traves de una IP en especifica.

Hay varios tipos de servicios como lo son: ClusterIP, NodePort, LoadBalancer.

- ClusterIP : Es el servicio por defecto y este no puede ser accedido desde el exterior, solamente desde dentro del cluster

- NodePort: Este servicio abre un puerto en un nodo en especifico para que pueda ser accedida nuestra aplicacion desde el exterior, por defecto trabaja puertos en un rango desde el 30000 hasta 32767.

- LoadBalancer: Este tipo sólo esta soportado en servicios de cloud público (Como por ejemplo Azure, Amazon Web services, entre otros. El proveedor asignara un recurso de balanceador de  carga para el acceso a los servicios. Este servicio tiene sus pros y contras:
  
  - Pros: Puede tener tu aplicacion en varios nodos y el balanceador va a encargarse de dirigir el trafico hacia ellas.
  
  - Contras: Al estar apuntando a una sola aplicacion en caso de que quieras exponer otra vas a tener que crear otro LB, y supongamos que tenemos 20 o 30 aplicaciones tendriamos 30 LB, esto se soluciona con un INGRESS que en cortas palabras es un controlador que se encarga de dirigir el trafico a la aplicacion correcta basandose en unas reglas en especifico Pero lo bueno de esto es que solo crea un punto de entrada.

Las IPs de los servicios son garantizadas, estas en teoria no deberian cambiar, pero todo depende del tipo de servicio.

- Port: es el puerto en el que el servicio va a estar escuchando

- TargetPort: Puerto a consumir dentro del pod

- EntryPoint: Es la conexion entre nuestro servicio y nuestros pods\

Por defecto si no especificamos un tipo de servicio va a ser ClusterIP

Para crear ejecutar el servicio de tipo ClusterIP

```
kubectl apply -f svc.yaml
```

Para crear ejecutar el servicio de tipo NodePort

```
kubectl apply -f nodeport.yaml
```

Para crear un pod de prueba

```
kubectl run podtest --image=nginx:alpine
```

Para acceder al Pod de prueba

```
kubectl exec -it podtest -- sh
```

Para ver las ips de los pods

```
kubectl get pod -o wide
```

Para describir el servicio

```
kubectl describe svc <serviceName>
```

Link del video en Youtube 

[Servicios en Kubernetes](https://youtu.be/GfqRKvOgd8E)

Mi pagina web:

[Kevo Rojas](https://kevorojas.com)
