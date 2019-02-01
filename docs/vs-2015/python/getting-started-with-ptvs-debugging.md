---
title: 'Introduzione a PTVS: Debug | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: b636dd4f3a5c5265231898573bfdf52de2dff84e
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834474"
---
# <a name="getting-started-with-ptvs-debugging"></a>Introduzione a PTVS: Debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debugger interattivo di Visual Studio consente di diagnosticare e risolvere facilmente i problemi nel codice Python.  
  
 È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
 Nell'argomento di introduzione precedente è stato creato un progetto di applicazione Python vuoto ed è stato immesso il codice seguente in PythonApplication1.py:  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 In genere quando si usa il codice in Visual Studio, l'esecuzione del codice viene avviata premendo F5.  Questo comando compila tutte le parti del progetto che devono essere compilate e avvia l'esecuzione del codice nel debugger.  È possibile premere CTRL+F5 per compilare e avviare il codice senza il debugger.  Con il debugger, il codice viene eseguito un po' più lentamente, ma in cambio si ottengono funzionalità di debug molto utili.  
  
 Il codice può anche essere avviato con il comando Esegui istruzione (in genere associato a F11).  È simile a F5, ma sospende l'esecuzione a ogni istruzione.  Se si vuole interrompere il programma a un certo punto, è possibile premere il pulsante sinistro del puntatore sul margine sinistro dell'editor di codice per impostare un punto di interruzione.  Quando si preme F5, l'esecuzione del programma verrà interrotta o arrestata in corrispondenza della riga con il punto di interruzione.  Il menu Debug contiene altre opzioni per l'esecuzione di istruzioni, ad esempio per eseguire l'istruzione/routine delle chiamate di funzione (F10), eseguire l'istruzione delle chiamate di funzione (F11) o saltare alla fine di una funzione (MAIUSC+F11).  
  
 Quando l'esecuzione viene interrotta nel debugger è possibile eseguire altre operazioni.  La finestra Variabili locali mostra i valori correnti delle variabili locali.  Man mano che vengono eseguite le istruzioni del codice, le variabili locali visualizzano automaticamente gli aggiornamenti.  La finestra Auto mostra le variabili accanto alla riga corrente in cui è stata interrotta l'esecuzione.  Nella finestra Espressioni di controllo è possibile digitare qualsiasi espressione Python che il debugger aggiornerà automaticamente ogni volta che l'esecuzione viene arrestata.  È anche possibile posizionare il puntatore sulle variabili nelle finestre dell'editor per visualizzare un popup dei valori della variabile e questo suggerimento dati consente di controllare gli oggetti.  Alcuni tipi di dati hanno visualizzatori speciali che sono accessibili dal suggerimento dati, ad esempio stringhe con una formattazione speciale come HTML, XML o JSON.  
  
 La finestra Stack di chiamate mostra le chiamate di funzione in sospeso che hanno portato all'istruzione corrente in cui il debugger è stato arrestato.  È possibile scegliere diversi stack frame (righe nello stack di chiamate) per passare al punto in cui il codice continuerà l'esecuzione in ogni funzione, cercherà un valore delle variabili e così via.  
  
 È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
## <a name="see-also"></a>Vedere anche  
 [Documentazione wiki](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [Video introduttivi e dettagliati su PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
