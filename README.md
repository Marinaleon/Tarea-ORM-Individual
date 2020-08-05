# Tarea-ORM-Individual
#python manage.py  shell
from Facturacion.models import *
Producto.objects.create(descripcion='Pepsy',precio=1.25,stock=180)
Producto.objects.create(descripcion='Chocolate',precio=0.45,stock=170)
Producto.objects.create(descripcion='Gomitas',precio=0.10,stock=70)
Producto.objects.create(descripcion='Vive 100',precio=1.25,stock=100)
Producto.objects.create(descripcion='Helado',precio=0.35,stock=750)
Producto.objects.create(descripcion='Confre de chocolate',precio=1.47,stock=1050)
P= Producto(descripcion='Aceite Girazol',precio=0.50,stock=50)
P.save()
P1= Producto(descripcion='Coca cola',precio=1.50,stock=100)
P1.save()
P2= Producto(descripcion='Tomate',precio=0.55,stock=200)
P2.save()
P3= Producto(descripcion='Detergente',precio=0.85,stock=22)
P3.save()
P4= Producto(descripcion='Desinfectante',precio=0.45,stock=25)
P4.save()
P5= Producto(descripcion='Jabon',precio=1.53,stock=24)
P5.save()


C1=Cliente(nombre='MARINA MAITE LEON LOJA',ruc='123456789',direccion='MILAGRO')
C1.producto_set=P1
C1.save()
C2=Cliente(nombre='LEON LOJA MARINA MAITE',ruc='123456890',direccion='MILAGRO')
C2.producto_set=P2
C2.save()
C3=Cliente(nombre='ELVIS LEON LOJA',ruc='147852369',direccion='MILAGRO')
C3.producto_set=P2
C3.save()
C4=Cliente(nombre='JOSTIN JAVIER LEON LOJA',ruc='123784560',direccion='MILAGRO')
C4.producto_set=P2
C4.save()
C5=Cliente(nombre='SILVIA LOJA',ruc='2315568463',direccion='MILAGRO')
C5.producto_set=P3
C5.save()
C6=Cliente.objects.create(nombre='NUEVO CLIENTE 1',ruc='123123123',direccion='MILAGRO')
C7=Cliente.objects.create(nombre='NUEVO CLIENTE 2',ruc='321321321',direccion='MILAGRO')
C8=Cliente.objects.create(nombre='NUEVO CLIENTE 3',ruc='345345345',direccion='MILAGRO')
C9=Cliente.objects.create(nombre='NUEVO CLIENTE 4',ruc='789456120',direccion='MILAGRO')


F1=Factura(cliente=C3,fecha='2020-08-01',total=50.01)
F1.save()
F2=Factura(cliente=C4,fecha='2020-08-10',total=20.10)
F2.save()
F3=Factura(cliente=C5,fecha='2020-08-01',total=12.00)
F3.save()
F4=Factura(cliente=C2,fecha='2020-08-10',total=13.50)
F4.save()
F5=Factura(cliente=C2,fecha='2020-07-10',total=10.50)
F5.save()
F6=Factura.objects.create(cliente=C2,fecha='2020-08-7',total=11.45)
F7=Factura.objects.create(cliente=C2,fecha='2019-08-7',total=11.00)
F8=Factura.objects.create(cliente=C3,fecha='2018-08-7',total=51.05)
F9=Factura.objects.create(cliente=C4,fecha='2017-08-7',total=41.00)
F10=Factura.objects.create(cliente=C4,fecha='2017-08-7',total=41.50)


d1=DetalleFactura(factura=F3,producto=P2,cantidad=2,precio=20.50,subtotal=20)
d1.save()
d2=DetalleFactura(factura=F4,producto=P3,cantidad=1,precio=0.50,subtotal=12.50)
d2.save()
d3=DetalleFactura(factura=F2,producto=P3,cantidad=2,precio=10.25,subtotal=12.50)
d3.save()
d4=DetalleFactura(factura=F2,producto=P4,cantidad=1,precio=1.2,subtotal=5.40)
d4.save()
d5=DetalleFactura.objects.create(factura=F6,producto=P5)
d6=DetalleFactura.objects.create(factura=F6,producto=P2)
d7=DetalleFactura.objects.create(factura=F5,producto=P4)
d8=DetalleFactura.objects.create(factura=F4,producto=P1)

P1 = Producto.objects.get(id=3)
P1.precio=2.50
P1.save()
P2 = Producto.objects.get(id=4)
P2.precio=2.50
P2.save()
Producto.objects.filter(id=1).update(precio=10.50)
Producto.objects.filter(id=2).update(precio=12.5)

C1 = Cliente.objects.get(id=1)
C1.direccion='LAS MARGARITAS'
C1.save()
C2 = Cliente.objects.get(id=2)
C2.direccion='LAS MARGARITAS 3'
C2.save()
Cliente.objects.filter(id=3).update(direccion='MARGARITAS 2')
Cliente.objects.filter(id=4).update(direccion='CENTRO')

F1 = Factura.objects.get(id=1)
F1.total=12.50
F1.save()

F2 = Factura.objects.get(id=2)
F2.total=16.50
F2.save()

Factura.objects.filter(id=3).update(total=25)
Factura.objects.filter(id=4).update(total=35)


d1 = DetalleFactura.objects.get(id=2)
d1.cantidad=2
d1.save()

d2 = DetalleFactura.objects.get(id=3)
d2.cantidad=1
d2.save()

DetalleFactura.objects.filter(id=1).update(cantidad=10)
DetalleFactura.objects.filter(id=4).update(cantidad=5)


P=Producto.objects.get(id=1)
P.delete()

Producto.objects.filter(id=2).delete()

C=Cliente.objects.get(id=1)
C.delete()

Cliente.objects.filter(id=2).delete()

F=Factura.objects.get(id=1)
F.delete()

Factura.objects.filter(id=2).delete()

D=DetalleFactura.objects.get(id=1)
D.delete()
DetalleFactura.objects.filter(id=2).delete()


p=Producto.objects.all()
p=Producto.objects.get(id=4)
Producto.objects.filter(id__lte=4)
Producto.objects.exclude(descripcion__icontains='Coca cola')
Producto.objects.filter(id__gte=5)
Producto.objects.filter(id__gt=5).values('id','descripcion')
Producto.objects.filter(id__lt=5).values('id','descripcion')
Producto.objects.filter(descripcion='Coca Cola').values('id','descripcion')

Factura.objects.filter(cliente__nombre='SILVIA LOJA')
c= Cliente.objects.get(nombre='SILVIA LOJA')
c.factura_set.all()
c.factura_set.filter(id=2)
Factura.objects.select_related('cliente').filter(cliente__nombre='SILVIA LOJA')
Cliente.objects.prefetch_related('producto').filter(nombre='SILVIA LOJA').values('nombre','producto__descripcion')
