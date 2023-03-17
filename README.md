# MaskRCNN_Video

En este proyecto abordaremos la segmentación semantica usando MaskRCNN en imagenes y video. Los repositorios base de este proyecto son los siguiente. El primero de ellos es la implementación para Tensorflow 1, y el segundo repositorio tiene la actualización para Tensorflow 2. el tercero de ellos
se realizaron modificaciones para correr la detección usando la cámara web. Por ultimo se implementaron metricas de validacion del modelo como Curva de Roc, Curva de lift, F1 score, Recall,Curva de Precision-Recall y matríz de confusión.

    https://github.com/matterport/Mask_RCNN
    https://github.com/akTwelve/Mask_RCNN
    https://github.com/DavidReveloLuna/MaskRCNN_Video

## Preparación del entorno

Prepararemos un entorno con python 3.7.7, Tensorflow 2.1.0 y keras 2.3.1

    $ conda create -n MaskRCNN anaconda python=3.7.7
    $ conda activate MaskRCNN
    $ conda install ipykernel
    $ python -m ipykernel install --user --name MaskRCNN --display-name "MaskRCNN"
    $ conda install tensorflow-gpu==2.1.0 cudatoolkit=10.1
    $ pip install tensorflow==2.1.0
    $ pip install jupyter
    $ pip install keras
    $ pip install numpy scipy Pillow cython matplotlib scikit-image opencv-python h5py imgaug IPython[all]
    
## Instalar MaskRCNN

    $ python setup.py install
    $ pip install git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI
    
## Prueba en Jupyter notebook

    $ cd samples
    $ jupyter notebook  
    
# Entrenamiento con custom-dataset
-   Etiquetar el data set con la herramienta [VIAv1.0](http://www.robots.ox.ac.uk/~vgg/software/via/via-1.0.0.html) (Hacerlo con la versión 1.0.0)
-   Guardar los datos de validación y entrenamiento en carpetas con nombre train, test y val
-   Guardar las anotaciones de los dos grupos de datos con el nombre: via_region_data.json
-   Ejeccutar en google colab el archivo Person.ipynb.

## Prueba del modelo entrenado con custom-dataset

-   PARA PRUEBA DEL SISTEMA CON IMÁGENES:
    
    Modificar los parámetros 
    
    -   model_filename = "mask_rcnn_persona_0050.h5" # Aquí deben cargar el modelo entrenado con su dataset
    -   class_names = ['BG', 'persona'] # Las clases relacionadas con su modelo BG + clases custom
    -   min_confidence = 0.6 # Nivel mínimo de confianza para aceptar un hallazgo como positivo  
    
        
-   PARA PRUEBA DEL SISTEMA EN VIDEO:

    Modificar los parámetros 
    
    -   model_filename = "mask_rcnn_persona_0050.h5" # Aquí deben cargar el modelo entrenado con su dataset
    -   class_names = ['BG', 'persona'] # Las clases relacionadas con su modelo BG + clases custom
    -   min_confidence = 0.6 # Nivel mínimo de confianza para aceptar un hallazgo como positivo
    -   camera = cv2.VideoCapture(0) # Si desean correr webcam
    -   camera = cv2.VideoCapture("video.mp4") # Si desean correr un video cargandolo desde su PC
    
    $ python personVideo.py    

 
## Entrenamiento multiclases custom dataset

 -   CustomClasses.ipynb
 
## IoU Intersection over Union

-   IoUTest.ipynb
## Prueba con dataset de imagenes de validacion
-   testImages.ipynb
-   IoUTest.ipynb ( al final del archivo se encuentra una validacion  en video en tiempo real, el modelo no esta entrenado para procesar imagenes en formato RGB pero aun asi logra detectar algo y segementar, el programa esta adaptado y entrenado para reconocimiento de imagenes adquiridas a partir de la nube de puntos de un LIDAR)
 
# Agradecimientos

    Matterport, Inc
    https://github.com/matterport

    Adam Kelly
    https://github.com/akTwelve

    DavidReveloLuna 
    https://github.com/DavidReveloLuna/MaskRCNN_Video

