---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-method
title: (C#) Refactoring Estrai metodo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 18fc4c20b39341f884fb23b51822ce7f6e427007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extract-method-refactoring-c"></a>Refactoring Estrai Metodo (C#)
**Estrai metodo** è un'operazione di refactoring che fornisce un modo semplice per creare un nuovo metodo da un frammento di codice in un membro esistente.  
  
 Utilizzando **Estrai metodo**, è possibile creare un nuovo metodo estraendo una selezione di codice all'interno del blocco di codice di un membro esistente. Il nuovo metodo estratto contiene il codice selezionato e il codice selezionato nel membro esistente viene sostituito con una chiamata al metodo di nuovo. Trasformare un frammento di codice in un proprio metodo consente di rapidamente e con precisione riorganizzare il codice per migliorarne il riutilizzo e la leggibilità.  
  
 **Estrai metodo** offre i vantaggi seguenti:  
  
-   Promuove codifica migliori sottolineando metodi distinti e riutilizzabili.  
  
-   Fornisce codice mediante una buona organizzazione autodocumentato.  
  
     Quando i nomi descrittivi sono metodi di alto livello possono ulteriori come una serie di commenti.  
  
-   Favorisce la creazione di metodi di granularità per semplificare l'override.  
  
-   Consente di ridurre la duplicazione del codice.  
  
### <a name="to-use-extract-method"></a>Per utilizzare Estrai metodo  
  
1.  Creare un'applicazione console denominata `ExtractMethod` quindi sostituire `Program` con il codice di esempio seguente.  
  
    ```csharp  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  Selezionare il frammento di codice che si desidera estrarre:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  Nel **refactoring** menu, fare clic su **Estrai metodo**.  
  
     Il **Estrai metodo** viene visualizzata la finestra di dialogo.  
  
     In alternativa, è anche possibile premere il tasto di scelta rapida CTRL + R, M per visualizzare il **Estrai metodo** la finestra di dialogo.  
  
     È possibile anche fare doppio clic al codice, scegliere **refactoring**e quindi fare clic su **Estrai metodo** per visualizzare il **Estrai metodo** la finestra di dialogo.  
  
4.  Specificare un nome per il nuovo metodo, ad esempio `CircleArea`nella **nuovo nome del metodo** casella.  
  
     Verrà visualizzata un'anteprima della firma del metodo di nuovo in **Anteprima firma del metodo**.  
  
5.  Fare clic su **OK**.  
  
## <a name="remarks"></a>Note  
 Quando si utilizza il **Estrai metodo** comando, viene inserito il nuovo metodo dopo il membro di origine nella stessa classe.  
  
## <a name="partial-types"></a>Tipi parziali  
 Se la classe è un tipo parziale, quindi **Estrai metodo** genera il nuovo metodo immediatamente dopo il membro di origine. **Estrai metodo** determina la firma del nuovo metodo, la creazione di un metodo statico quando nessun dato istanza fa riferimento il codice nel nuovo metodo.  
  
## <a name="generic-type-parameters"></a>Parametri di tipo generico  
 Quando si estrae un metodo che presenta un parametro di tipo generico non vincolato, il codice generato non verrà aggiunto il `ref` modificatore a tale parametro a meno che non venga assegnato un valore. Se il metodo estratto supporta tipi di riferimento come argomento di tipo generico, è necessario aggiungere manualmente il `ref` modificatore al parametro nella firma del metodo.  
  
## <a name="anonymous-methods"></a>Metodi anonimi  
 Se si tenta di estrarre una parte di un metodo anonimo che include un riferimento a una variabile locale dichiarata o a cui fa riferimento all'esterno del metodo anonimo, quindi Visual Studio notificherà eventuali modifiche nella semantica.  
  
 Quando un metodo anonimo viene utilizzato il valore di una variabile locale, il valore viene ottenuto al momento che viene eseguito il metodo anonimo. Quando un metodo anonimo viene estratto in un altro metodo, il valore della variabile locale viene ottenuto al momento della chiamata al metodo estratto.  
  
 Nell'esempio seguente viene illustrata questa modifica semantica. Se si esegue questo codice, quindi **11** verranno stampati sulla console. Se si utilizza **Estrai metodo** per estrarre l'area di codice contrassegnata da commenti del codice nel relativo metodo e quindi eseguire il codice sottoposto a refactoring, quindi **10** verranno stampati sulla console.  
  
```csharp  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 Per risolvere questo problema, verificare le variabili locali che vengono utilizzate nei campi di un metodo anonimo della classe.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](refactoring-csharp.md)