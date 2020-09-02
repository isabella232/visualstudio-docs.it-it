---
title: Refactoring Incapsula campo (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667563"
---
# <a name="encapsulate-field-refactoring-c"></a>Refactoring Incapsula campo (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'operazione di refactoring **Incapsula campo** consente di creare rapidamente una proprietà da un campo esistente e quindi di aggiornare facilmente il codice con riferimenti alla nuova proprietà.

 Quando un [campo](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) è [pubblico](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), altri oggetti hanno accesso diretto a tale campo e possono modificarlo, non rilevato dall'oggetto proprietario di tale campo. Utilizzando le [Proprietà](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) per incapsulare il campo, è possibile impedire l'accesso diretto ai campi.

 Per creare la nuova proprietà, l'operazione **Incapsula campo** modifica il modificatore di accesso per il campo che si vuole incapsulare su [privato](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)e quindi genera funzioni di accesso [Get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) e [set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) per quel campo. In alcuni casi, viene generata una sola funzione di accesso `get`, ad esempio quando il campo viene dichiarato di sola lettura.

 Il motore di refactoring aggiorna il codice con riferimenti alla nuova proprietà nelle aree specificate nella sezione **Update references** della finestra di dialogo **Incapsula campo** .

### <a name="to-create-a-property-from-a-field"></a>Per creare una proprietà da un campo

1. Creare un'applicazione console denominata `EncapsulateFieldExample` quindi sostituire `Program` con il codice di esempio seguente.

    ```csharp
    class Square
    {
        // Select the word 'width' and then use Encapsulate Field.
        public int width, height;
    }
    class MainClass
    {
        public static void Main()
        {
            Square mySquare = new Square();
            mySquare.width = 110;
            mySquare.height = 150;
            // Output values for width and height.
            Console.WriteLine("width = {0}", mySquare.width);
            Console.WriteLine("height = {0}", mySquare.height);
        }
    }
    ```

2. Nell' [editor di codice](../ide/writing-code-in-the-code-and-text-editor.md)posizionare il cursore nella dichiarazione sul nome del campo che si desidera incapsulare. Nell'esempio seguente, posizionare il cursore sulla parola `width`:

    ```csharp
    public int width, height;
    ```

3. Scegliere **Incapsula campo**dal menu **refactoring** .

     Verrà visualizzata la finestra di dialogo **Incapsula campo** .

     È anche possibile digitare il tasto di scelta rapida CTRL + R, E per visualizzare la finestra di dialogo **Incapsula campo** .

     È anche possibile fare clic con il pulsante destro del mouse sul cursore, scegliere **refactoring**, quindi fare clic su **Incapsula campo** per visualizzare la finestra di dialogo **Incapsula campo** .

4. Specificare le impostazioni.

5. Premere INVIO oppure fare clic sul pulsante **OK** .

6. Se è stata selezionata l'opzione **Anteprima modifiche riferimento** , viene visualizzata la finestra **Anteprima modifiche riferimenti** . Fare clic sul pulsante **Applica**.

     Nel file di origine verrà visualizzato il codice delle funzioni di accesso `get` e `set` seguenti:

    ```csharp
    public int Width
    {
        get { return width; }
        set { width = value; }
    }
    ```

     Anche il codice nel metodo `Main` viene aggiornato in base al nuovo nome della proprietà `Width`.

    ```csharp
    Square mySquare = new Square();
    mySquare.Width = 110;
    mySquare.height = 150;
    // Output values for width and height.
    Console.WriteLine("width = {0}", mySquare.Width);
    ```

## <a name="remarks"></a>Osservazioni
 L'operazione **Incapsula campo** è possibile solo quando il cursore è posizionato sulla stessa riga della dichiarazione del campo.

 Per le dichiarazioni che dichiarano più campi, **Incapsula campo** usa la virgola come limite tra i campi e avvia il refactoring sul campo più vicino al cursore e sulla stessa riga del cursore. È inoltre possibile specificare il campo che si desidera incapsulare selezionandone il nome nella dichiarazione.

 Il codice generato da questa operazione di refactoring viene modellato dalla funzionalità di frammenti di codice per Incapsula campo. I frammenti di codice sono modificabili. Per altre informazioni, vedere [Code Snippets](../ide/code-snippets.md) (Frammenti di codice).

## <a name="see-also"></a>Vedere anche
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md) [frammenti di codice Visual C#](../ide/visual-csharp-code-snippets.md)