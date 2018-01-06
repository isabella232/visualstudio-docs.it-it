---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: Incapsula campo Refactoring (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: d587edebcea443e0bfff52004b128c70923470d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="encapsulate-field-refactoring-c"></a>Refactoring Incapsula campo (C#)
Il **Incapsula campo** operazione di refactoring consente di creare rapidamente una proprietà da un campo esistente e quindi aggiornare facilmente il codice con riferimenti nella nuova proprietà.  
  
 Quando un [campo](/dotnet/csharp/programming-guide/classes-and-structs/fields) è [pubblica](/dotnet/csharp/language-reference/keywords/public), altri oggetti possono accedere direttamente a tale campo e modificarlo, senza essere rilevati dall'oggetto a cui appartiene il campo. Utilizzando [proprietà](/dotnet/csharp/programming-guide/classes-and-structs/properties) per incapsulare quel campo, è possibile impedire l'accesso diretto ai campi.  
  
 Per creare la nuova proprietà, il **Incapsula campo** operazione cambia il modificatore di accesso per il campo che si desidera incapsulare su [privata](/dotnet/csharp/language-reference/keywords/private), quindi genera [ottenere](/dotnet/csharp/language-reference/keywords/get)e [impostare](/dotnet/csharp/language-reference/keywords/set) funzioni di accesso per tale campo. In alcuni casi, viene generata una sola funzione di accesso `get`, ad esempio quando il campo viene dichiarato di sola lettura.  
  
 Il motore di refactoring di aggiornare il codice con i riferimenti alla nuova proprietà nelle aree specificate nella **Aggiorna riferimenti** sezione la **Incapsula campo** la finestra di dialogo.  
  
### <a name="to-create-a-property-from-a-field"></a>Per creare una proprietà da un campo  
  
1.  Creare un'applicazione console denominata `EncapsulateFieldExample` quindi sostituire `Program` con il codice di esempio seguente.  
  
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
  
2.  Nel [Editor di codice](../ide/writing-code-in-the-code-and-text-editor.md), posizionare il cursore nella dichiarazione, il nome del campo che si desidera incapsulare. Nell'esempio seguente, posizionare il cursore sulla parola `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  Nel **refactoring** menu, fare clic su **Incapsula campo**.  
  
     Il **Incapsula campo** viene visualizzata la finestra di dialogo.  
  
     È anche possibile premere il tasto di scelta rapida CTRL + R, E per visualizzare il **Incapsula campo** la finestra di dialogo.  
  
     È anche possibile fare doppio clic sul cursore, scegliere **refactoring**, quindi fare clic su **Incapsula campo** per visualizzare il **Incapsula campo** la finestra di dialogo.  
  
4.  Specificare le impostazioni.  
  
5.  Premere INVIO oppure fare clic su di **OK** pulsante.  
  
6.  Se si seleziona il **Anteprima modifiche riferimento** opzione, il **Anteprima modifiche riferimento** verrà visualizzata la finestra. Fare clic su di **applica** pulsante.  
  
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
  
## <a name="remarks"></a>Note  
 Il **Incapsula campo** operazione è possibile solo quando il cursore viene posizionato sulla stessa riga della dichiarazione di campo.  
  
 Per più campi, le dichiarazioni **Incapsula campo** utilizza la virgola come limite tra i campi e avvia l'operazione di refactoring nel campo più vicino al cursore e sulla stessa riga del cursore. È inoltre possibile specificare il campo che si desidera incapsulare selezionandone il nome nella dichiarazione.  
  
 Il codice generato da questa operazione di refactoring viene modellato dalla funzionalità di frammenti di codice per Incapsula campo. I frammenti di codice sono modificabili. Per altre informazioni, vedere [Code Snippets](../ide/visual-csharp-code-snippets.md) (Frammenti di codice).  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](refactoring-csharp.md)   
 [Frammenti di codice Visual C#](../ide/visual-csharp-code-snippets.md)