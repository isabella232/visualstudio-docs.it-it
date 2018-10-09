---
title: Controllo della visibilità di un'icona o un elemento Decorator | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9cc74f7ba8c71c2b8828ad19c4d6af80d6e8b8e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517036"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controllo della visibilità di un'icona o di un elemento Decorator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [controllo della visibilità di un'icona o un elemento Decorator](https://docs.microsoft.com/visualstudio/modeling/controlling-the-visibility-of-an-icon-or-decorator).  
  
Oggetto *decorator* è un'icona o una riga di testo che viene visualizzato in una forma in un linguaggio specifico di dominio (DSL). È possibile visualizzare l'elemento decorator e scompaiano a seconda dello stato delle proprietà nel modello. In una forma che rappresenta una persona, ad esempio, si potrebbero hanno icone diverse che vengono visualizzati in base alla relativa al sesso dell'utente, numero di elementi figlio e così via.  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controllo della visibilità di un'icona o un elemento decorator  
 La procedura seguente presuppone che già definito una forma e il relativo mapping a una classe di dominio. Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Per controllare la visibilità di un elemento decorator di icona o di testo  
  
1.  Nel diagramma di definizione DSL, aggiungere alla classe di forma di icone o gli elementi Decorator di testo che si desidera visualizzare.  
  
    1.  Fare doppio clic la classe di forma, scegliere **Add**e quindi scegliere il tipo obbligatorio dell'elemento decorator.  
  
    2.  Impostare l'elemento decorator **posizione** proprietà. Più di un elemento decorator può avere la stessa posizione. Ad esempio, si potrebbe avere icone Launcher per maschio e femmina nella stessa posizione di condivisione.  
  
    3.  Impostare il **icona predefinita** proprietà di un elemento decorator di icona.  
  
2.  Selezionare la mappa elementi diagramma, ovvero la linea grigia tra la classe di forma e la classe di dominio nel diagramma di definizione DSL.  
  
3.  Nella finestra Dettagli DSL nel **mappe elementi Decorator** scheda, selezionare un elemento decorator. Ad esempio, il MaleDecorator.  
  
4.  Verificare i **filtro di visibilità** casella.  
  
5.  Se la proprietà di dominio che debba controllare la visibilità è nella classe di dominio immediato, lasciare **percorso di proprietà Filter** vuoto.  
  
     In caso contrario, fare clic sul menu a discesa e passare alla classe in cui si trova la proprietà o relazioni.  
  
    -   Per evitare una segnalazione di errore, non devono passare tramite una relazione contrassegnata con "*" nello strumento di navigazione.  
  
6.  Impostare il **proprietà Filter** a una proprietà di dominio. Ad esempio, il sesso.  
  
7.  Nel **voci visibilità** elencare, aggiungere i valori di questa proprietà di dominio per il quale deve essere visibile l'elemento decorator. Ad esempio, Male.  
  
8.  Ripetere i passaggi per ogni icona.  
  
9. **Trasforma tutti i modelli**, compilare ed eseguire e aprire un diagramma di test.  
  
10. Quando si modifica il valore della proprietà controllo, gli elementi Decorator visualizzato che non vengono più visualizzati.  
  
 Spesso, è consigliabile visibilità da parte di una formula più complessa rispetto a un semplice set di valori. Ad esempio, per avere un'icona dipendono dal numero di collegamenti di un tipo specifico o per renderla variano a seconda che un un numero è in un intervallo specifico. In tal caso, utilizzare la procedura seguente.  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Controllare la visibilità di un elemento decorator in base a una formula  
  
1.  Aggiungere una proprietà calcolata del dominio per la classe di dominio. Nel **proprietà** finestra, impostare i valori seguenti:  
  
     **IsBrowsable =**`False`**-questo modo si nasconde la proprietà da parte dell'utente**  
  
     **Tipo =**`Calculated`**-questo significa che verrà fornito il codice che calcola il proprio valore**  
  
     **Nome** ad esempio **DecoratorControl**  
  
     **Tipo** = `Boolean`  
  
     Per altre informazioni, vedere [calcolate e le proprietà di archiviazione personalizzate](../modeling/calculated-and-custom-storage-properties.md).  
  
2.  Verificare la nuova proprietà di controllare la visibilità dell'elemento decorator.  
  
    1.  Selezionare la mappa elementi diagramma, ovvero la linea grigia dalla classe di dominio alla forma. Nel **dettagli DSL** finestra, aprire il **DecoratorMap** scheda.  
  
    2.  Verificare i **filtro di visibilità** casella.  
  
    3.  Nelle **proprietà Filter**, selezionare la proprietà del controllo **DecoratorControl**.  
  
    4.  Sotto **voci visibilità**, immettere `True`.  
  
3.  Fare clic su **Trasforma tutti i modelli** sulla barra degli strumenti Esplora soluzioni.  
  
4.  Fare clic su **Compila soluzione** nel **compilazione** menu.  
  
5.  Fare doppio clic sulla segnalazione di errori che è apparsa: "*ClasseUtente* non contiene una definizione per GetDecoratorControlValue...".  
  
     Consente di aprire l'editor di testo in dsl\generatedcode\domainclasses.cs. Il messaggio di errore evidenziato precedente è un commento che viene chiesto di aggiungere un metodo.  
  
6.  Si noti lo spazio dei nomi, classe e sul metodo che non sono presenti.  Ad esempio, Company.FamilyTree.Person.GetDecoratorControlValue().  
  
7.  In un file di codice separato, scrivere una definizione di classe parziale che contiene il metodo mancante. Ad esempio:  
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     Per altre informazioni sulla personalizzazione del modello con il codice del programma, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
8.  Ricompilare ed eseguire la soluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md)   
 [Impostazione di un'immagine di sfondo in un diagramma](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)


