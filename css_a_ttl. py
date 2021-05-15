# importar el módulo CSV para tratar con archivos CSV
import csv

# crear una variable de 'reader', que nos permita jugar con el contenido del archivo CSV
# para hacer eso, crear la variable ifile, abrimos el archivo CSV en eso, luego pasamos su contenido a la variable del lector.
ifile = open('/content/drive/MyDrive/coviddata.csv', 'rt')
reader = csv.reader(ifile)


# crea una nueva variable llamada 'outfile' (podría ser cualquier nombre), que usaremos para crear un nuevo archivo al que pasaremos nuestro TTL.
outfile = open('casoscovid.ttl', 'a')

# Encabezado
outfile.write('@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .\n')
outfile.write('@prefix bsbm: <http://www4.wiwiss.fu-berlin.de/bizer/bsbm/v01/vocabulary/> .\n')
outfile.write('@prefix dc: <http://purl.org/dc/elements/1.1/> .\n')
outfile.write('@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .\n\n')


# hacer que Python recorra cada fila en el CSV e ignore la primera fila.
rownum = 0
for row in reader:
    if rownum == 0:
        pass
    else:  # si no es la primera fila, coloque el contenido de la fila en la variable 'c', luego cree una variable 'd' con las cosas que queremos en el archivo.
        c = row

        d = 'dataFromRegion:' + c[0] + '\n' \
            'rdf:type bsbm:Region ; \n' \
            'bsbm: TotalCasos(+) ' + '"' + c[1] + '"' + '^^xsd:Integer ;\n' \
            'bsbm: Fallecidos ' + '"' + c[2] + '"' + '^^xsd:Integer ;\n' \


        outfile.write(d)  # ahora escribe la variable d en el archivo
    rownum += 1  # avanza el número de fila para que podamos recorrer de nuevo con la siguiente fila

# Termina cerrando los dos archivos que creamos

outfile.close()
ifile.close()
