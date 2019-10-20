---
title: Refactoring Estrai metodoC#() | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667549"
---
# <a name="extract-method-refactoring-c"></a>Refactoring Estrai Metodo (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Estrai metodo** è un'operazione di refactoring che fornisce un modo semplice per creare un nuovo metodo da un frammento di codice in un membro esistente.

 Usando il **Metodo Extract**è possibile creare un nuovo metodo estraendo una selezione di codice dall'interno del blocco di codice di un membro esistente. Il nuovo metodo estratto contiene il codice selezionato e il codice selezionato nel membro esistente viene sostituito con una chiamata al nuovo metodo. Trasformare un frammento di codice nel proprio metodo consente di riorganizzare rapidamente e accuratamente il codice per una migliore riutilizzo e leggibilità.

 Il **Metodo Extract** presenta i vantaggi seguenti:

- Incoraggia le procedure di codifica migliori enfatizzando metodi discreti e riutilizzabili.

- Incoraggia il codice autodocumentato attraverso una corretta organizzazione.

     Quando si usano nomi descrittivi, i metodi di alto livello possono leggere più come una serie di commenti.

- Incoraggia la creazione di metodi con granularità fine per semplificare l'override.

- Riduce la duplicazione del codice.

### <a name="to-use-extract-method"></a>Per utilizzare il metodo Extract

1. Creare un'applicazione console denominata `ExtractMethod` quindi sostituire `Program` con il codice di esempio seguente.

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

2. Selezionare il frammento di codice che si vuole estrarre:

    ```csharp
    double area = PI * radius * radius;
    ```

3. Scegliere **Estrai metodo**dal menu **refactoring** .

     Verrà visualizzata la finestra di dialogo **Estrai metodo** .

     In alternativa, è anche possibile digitare il tasto di scelta rapida CTRL + R, M per visualizzare la finestra di dialogo **Estrai metodo** .

     È anche possibile fare clic con il pulsante destro del mouse sul codice selezionato, scegliere **refactoring**, quindi fare clic su **Estrai metodo** per visualizzare la finestra di dialogo **Estrai metodo** .

4. Specificare un nome per il nuovo metodo, ad esempio `CircleArea`, nella casella **nuovo nome metodo** .

     Viene visualizzata un'anteprima della firma del nuovo metodo sotto la **firma del metodo di anteprima**.

5. Fare clic su **OK**.

## <a name="remarks"></a>Note
 Quando si usa il comando **Estrai metodo** , il nuovo metodo viene inserito dopo il membro di origine nella stessa classe.

## <a name="partial-types"></a>Tipi parziali
 Se la classe è un tipo parziale, il **Metodo Extract** genera il nuovo metodo immediatamente successivo al membro di origine. **Estrai metodo** determina la firma del nuovo metodo, creando un metodo statico quando il codice nel nuovo metodo non fa riferimento a dati di istanza.

## <a name="generic-type-parameters"></a>Parametri di tipo generico
 Quando si estrae un metodo con un parametro di tipo generico non vincolato, il codice generato non aggiungerà il modificatore `ref` a tale parametro a meno che non venga assegnato un valore. Se il metodo estratto supporta i tipi di riferimento come argomento di tipo generico, è necessario aggiungere manualmente il modificatore `ref` al parametro nella firma del metodo.

## <a name="anonymous-methods"></a>Metodi anonimi
 Se si tenta di estrarre parte di un metodo anonimo che include un riferimento a una variabile locale dichiarata o a cui viene fatto riferimento all'esterno del metodo anonimo, Visual Studio avviserà le potenziali modifiche semantiche.

 Quando un metodo anonimo usa il valore di una variabile locale, il valore viene ottenuto nel momento in cui viene eseguito il metodo anonimo. Quando un metodo anonimo viene estratto in un altro metodo, il valore della variabile locale viene ottenuto al momento della chiamata al metodo estratto.

 Nell'esempio seguente viene illustrata questa modifica semantica. Se questo codice viene eseguito, **11** verrà stampato sulla console. Se si usa il **Metodo Extract** per estrarre l'area di codice contrassegnata dai commenti del codice nel proprio metodo e quindi eseguire il codice sottoposto a refactoring, **10** verrà stampato nella console.

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

 Per ovviare a questa situazione, creare le variabili locali usate nei campi del metodo anonimo della classe.

## <a name="see-also"></a>Vedere anche
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)