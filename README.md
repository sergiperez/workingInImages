# Treballant sobre imatges

## Exercici 1 - Detectar si són imatges o no

![](https://http.cat/415.jpg)

El primer que heu de fer és netejar el directori imatges. Heu de llistar tots els arxius que hi ha en el directori i mostrar els noms dels arxius que no són imatges.

Per detectar si un fitxer és una imatge ho podeu fer de dues maneres:

- Detectar si l'extensió del fitxer, caràcters després del punt estan en el format correcte o no.
```python3=
correctFormats = ['rgb', 'gif','tiff','jpeg','jpg','bmp','png']
file = "hola.txt"
if file not in correctFormats:
    #TODO tractar arxiu sinó és iamtge
```
- **Però que passa si poso un fitxer i li poso extensió .jpg o .png** doncs que colaria, una millor manera es usant excepcions:
```python3=
from PIL import Image
try:
    img = Image.open('/home/mdriscoll/Pictures/all_python.jpg')
exception:
    #Aquí salta si no pot crear imatge i aquí s'ha de fer el codi per tracatar el fitxer no iamtge
```


Els formats correcte són:
'rgb', 'gif','tiff','jpeg','jpg','bmp' i 'png'.
Fora d'aquests formats haureu de preguntar a l'usuari si aquell arxiu vol:

- borrar
- moure'l a la carpeta noimages.

Heu d'executar l'acció que us demani l'usuari i seguir mostrant arxius.

Un cop heu netejat el directori imatges li mostreu el següent menu:

1. Seleccionar imatges per mida
2. Crear miniatures
3. Posar marca d'aigua
4. Convertir de png a jgp

## Exercici 2 - Triar imatges per mides

![](https://http.cat/414.jpg)

Heu de demanar a l'usuari per quina dimensió vol filtar:
- amplada (w)
- alçada (h)

Després preguntar-li quin és el mínim de píxels.
Aleshores crear una carpeta de nom seleccio(WoH)(NumPixels) (per exemple si ha entrat amplada i 300 px, la carpeta es dirà seleccioW300 ) i copiar allà les imatges de la carpeta images que compleixen aquestes condicions.

Per crear una carpeta en Python:

```python3=
import os
os.mkdir(path)
```

Per detectar mides d'una imatge:

```python3=
from PIL import Image 

filename = "image.png"
with Image.open(filename) as image: 
    width, height = image.size 
```

On a width guarda l'amplada i height l'alçada.

## Exercici 3 - Crear miniatures
![](https://memeguy.com/photos/images/mrw-i-click-the-link-and-its-the-same-size-as-the-thumbnail-9232.gif)

Heu de demanar a l'usuari quines mides han de tenir les miniatures, tant en alçada com amplada.

Després crear una carpeta que es dirà thumbnail i copiar allà les imatges redimensionades.

Aquí teniu un exemple com redimensionar:
```python3=
def main(): 
	try: 
		#Relative Path 
		img = Image.open("picture.jpg") 
		
		#In-place modification 
		img.thumbnail((200, 200)) 
		
		img.save("thumb.jpg") 
	except IOError: 
		pass

if __name__ == "__main__": 
	main()
```

## Exercici 4 - Posar marca d'aigua

![](https://i.imgflip.com/37i9vn.jpg)

Heu de demanar a l'usuari on està la imatge que voleu que posi com  a marca d'aigua. En aquest cas usarem la marca/logo.png .

I després li heu de dir on vol que la poseu, a quina cantonada:
- a dalt a l'esquerra
- a dalt a la dreta
- a baix a l'esquerra
- a baix a la dreta

Heu de crear una carpeta que es digui marcaAigua i allà guardareu les imatges amb la marca d'aigua.

Fixeu-vos aquí com posar una imatge dins una altra. fixeu-vos que al fer el paste indiqueu on la voleu situar:

```python3=
from PIL import Image 

def main(): 
	try: 
		#Relative Path 
		#Image on which we want to paste 
		img = Image.open("picture.jpg") 
		
		#Relative Path 
		#Image which we want to paste 
		img2 = Image.open("picture2.jpg") 
		img.paste(img2, (50, 50)) 
		
		#Saved in the same relative location 
		img.save("pasted_picture.jpg") 
		
	except IOError: 
		pass

if __name__ == "__main__": 
	main() 

##An additional argument for an optional image mask image is also available. 

```

## Exercici 5 - Desenvolupar l'opció del menú "Convertir png a jpg"

![](https://img.memecdn.com/PNG-vs-JPEG_o_23487.jpg)

Heu de convertir totes les imatges png, que hi ha a la carpeta images, a jpg.  Aquestes imatges convertides s'han de guardar en la carpeta jpg.

```python3=
from PIL import Image

im = Image.open("Ba_b_do8mag_c6_big.png")
rgb_im = im.convert('RGB')
rgb_im.save('colors.jpg')
```

