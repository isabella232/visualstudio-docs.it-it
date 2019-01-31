---
title: 'Introduzione a PTVS: Modifica del codice | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 2e883970b4b265b1864d53ef6e1f347160e5aeb9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758400"
---
# <a name="getting-started-with-ptvs-editing-code"></a>Introduzione a PTVS: Modifica del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS offre l'esperienza produttiva di editor di Visual Studio per Python.  
  
 È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Iniziare con il modello di progetto di applicazione Python vuoto di base.  
  
 Iniziare a digitare una riga `from … import` nell'editor.  Verrà visualizzato un popup con un elenco di completamento contenente tutti i moduli disponibili per l'importazione.  Questo elenco varia a seconda della versione di Python e delle librerie installate.  Usare la libreria matematica come esempio.  Si potrà notare che mentre si digita, l'elenco dei completamenti viene filtrato in base a tali elementi, inclusi i caratteri digitati.  Completare l'istruzione importando l'identificatore `sin`.  
  
```python  
from math import sin  
  
```  
  
 Durante la scrittura del codice, se si usa un identificatore che non è associato ma è presente nelle librerie, PTVS visualizza un popup con una correzione rapida per aggiungere l'istruzione di importazione appropriata necessaria.  Ad esempio, se è stato digitato `cos`, verrà visualizzato **Importa da math** offerto.  
  
 È possibile usare un frammento di codice per generare il codice.  Scegliere IntelliSense dal menu Modifica, quindi Inserisci frammento di codice.  Ora scegliere Python e quindi def.  Chiamare la funzione `make_dot_string` e aggiungere un parametro `x`.  È ora possibile aggiungere le asserzioni al file per lo sviluppo basato su test e si noterà che PTVS è già in grado di visualizzare la nuova funzione negli elenchi di completamento.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Tornare ora alla nuova funzione e iniziare a scrivere il corpo seguente:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Si noterà che PTVS presuppone che il parametro sia un numero intero perché ha analizzato i siti di chiamata in base a questa funzione.   È necessario usare anche la correzione rapida per importare `radians`.  
  
 Usare un altro frammento di codice per creare un blocco principale digitando `main` al livello superiore, richiamando l'interfaccia utente con gli smart tag utente e usando TAB per scegliere "def main ..."  Scrivere un ciclo di base per chiamare `make_dot_string`.  Si noterà che PTVS conosce la funzione in base alla quale viene restituita una stringa se si preme punto e verranno visualizzati i completamenti disponibili.  Questo tipo di informazioni scorrerà in tutto programma, in modo tale che sia possibile fornire le descrizioni comandi e i completamenti che consentono di comprendere e scrivere meglio il codice indipendentemente da dove terminano i valori.  
  
 Aggiungere una chiamata alla funzione di stampa per ottenere una funzione main simile alla seguente:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Se si preme F5, il codice viene eseguito in una finestra cmd.exe e viene visualizzato un punto che oscilla avanti e indietro.  
  
 È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Vedere anche  
 [Documentazione wiki](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [Video introduttivi e dettagliati su PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
