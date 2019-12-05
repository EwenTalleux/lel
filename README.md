# lel
import src.Competitor as Competitor
import Time

f=open("data/small_inscrits.csv","r")
champs=f.readline().rstrip().split(";")
lignes=f.readlines()
table=[]
for ligne in lignes:
    liste=ligne.rstrip().split(';')
    table.append(tuple(liste))
f.close()

dicti={}
def read_competitors(stri):
    try :
        f=open(stri,"r")
        champs=f.readline().rstrip().split(";")
        lignes=f.readlines()
        count=0
        for ligne in lignes:
            liste=ligne.rstrip().split(';')
            count+=1
            dicti[count]=Competitor.create(liste[0],liste[1],liste[2],liste[3],count)
        f.close()
    except FileNotFoundError:
        return("Aucun fichier ou répertoire : "+stri)
    
    return dicti

def affichage(t):
    for comp in t:
        print(Competitor.to_string(t[comp]))
    
    
