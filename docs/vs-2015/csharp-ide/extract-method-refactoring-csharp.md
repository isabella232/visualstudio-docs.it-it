---
title: Extrahovat Metodu Refactoring (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2d38c46d630f7deccaec8c093c2c4e75456eec0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954709"
---
# <a name="extract-method-refactoring-c"></a>Refactoring Estrai Metodo (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extrahovat Metodu** è un'operazione di refactoring che fornisce un modo semplice per creare un nuovo metodo da un frammento di codice in un membro esistente.  
  
 Usando **Estrai metodo**, è possibile creare un nuovo metodo estraendo una selezione di codice all'interno del blocco di codice di un membro esistente. Il nuovo metodo estratto contiene il codice selezionato e il codice selezionato nel membro esistente viene sostituito con una chiamata al metodo di nuovo. La disattivazione di un frammento di codice nel relativo metodo consente rapidamente e accuratamente riorganizzare il codice per migliorarne il riutilizzo e la leggibilità.  
  
 **Extrahovat Metodu** offre i vantaggi seguenti:  
  
-   Incoraggia procedure consigliate di codifica migliori da mettere in evidenza metodi distinti e riutilizzabili.  
  
-   Fornisce codice all'interno dell'organizzazione buona autodocumentato.  
  
     Quando i nomi descrittivi sono metodi di alto livello possono Scopri di più come una serie di commenti.  
  
-   Favorisce la creazione di metodi di granularità per semplificare l'override.  
  
-   Consente di ridurre la duplicazione del codice.  
  
### <a name="to-use-extract-method"></a>Usare Estrai metodo  
  
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
  
2.  Selezionare il frammento di codice da estrarre:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  Nel **refactoring** menu, fare clic su **Estrai metodo**.  
  
     Il **Estrai metodo** verrà visualizzata la finestra di dialogo.  
  
     In alternativa, è anche possibile premere il tasto di scelta rapida CTRL + R, M per visualizzare il **Estrai metodo** nella finestra di dialogo.  
  
     È possibile anche fare doppio clic selezionati di codice, scegliere **effettuare il refactoring**e quindi fare clic su **Estrai metodo** per visualizzare il **Estrai metodo** nella finestra di dialogo.  
  
4.  Specificare un nome per il nuovo metodo, ad esempio `CircleArea`, nella **nuovo nome del metodo** casella.  
  
     Consente di visualizzare un'anteprima della firma del metodo nuovo sotto **Anteprima firma metodo**.  
  
5.  Fare clic su **OK**.  
  
## <a name="remarks"></a>Note  
 Quando si usa la **Estrai metodo** comando, viene inserito il nuovo metodo dopo il membro di origine nella stessa classe.  
  
## <a name="partial-types"></a>Tipi parziali  
 Se la classe è un tipo parziale, quindi **Estrai metodo** genera il nuovo metodo immediatamente dopo il membro di origine. **Extrahovat Metodu** determina la firma del nuovo metodo, la creazione di un metodo statico quando i dati dell'istanza non viene fatto riferimento dal codice nel nuovo metodo.  
  
## <a name="generic-type-parameters"></a>Parametri di tipo generico  
 Quando si estrae un metodo che presenta un parametro di tipo generico non vincolato, il codice generato non verrà aggiunto il `ref` modificatore di parametro a meno che non venga assegnato un valore. Se il metodo estratto supporterà i tipi di riferimento come argomento di tipo generico, quindi è necessario aggiungerli manualmente il `ref` modificatore al parametro nella firma del metodo.  
  
## <a name="anonymous-methods"></a>Metodi anonimi  
 Se si tenta di estrarre una parte di un metodo anonimo che include un riferimento a una variabile locale dichiarata o fare riferimento all'esterno del metodo anonimo, quindi Visual Studio avviserà l'utente sulle modifiche nella semantica potenziali.  
  
 Quando un metodo anonimo Usa il valore di una variabile locale, il valore viene ottenuto nel momento in cui che viene eseguito il metodo anonimo. Quando un metodo anonimo viene estratto in un altro metodo, il valore della variabile locale viene ottenuto al momento della chiamata al metodo estratto.  
  
 Nell'esempio seguente viene illustrata questa modifica semantica. Se si esegue questo codice, quindi **11** verranno stampati sulla console. Se si usa **Estrai metodo** per estrarre l'area di codice contrassegnato dai commenti nel codice in un metodo e quindi eseguire il codice sottoposto a refactoring, quindi **10** verranno stampati sulla console.  
  
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
  
 Per risolvere questo problema, rendere le variabili locali che vengono usate i campi di metodo anonimo della classe.  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)