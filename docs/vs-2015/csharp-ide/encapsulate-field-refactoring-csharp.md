---
title: Incapsula campo Refactoring (C#) | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ee56c4588bbbd3ec5cfca03bbd18c6dec1732fbf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964949"
---
# <a name="encapsulate-field-refactoring-c"></a>Refactoring Incapsula campo (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il **Incapsula campo** operazione di refactoring consente di creare rapidamente una proprietà da un campo esistente e quindi aggiornare facilmente il codice con riferimenti alla nuova proprietà.  
  
 Quando un [campo](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) viene [pubblico](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), altri oggetti hanno accesso diretto a tale campo e modificarlo, senza essere rilevati dall'oggetto a cui appartiene il campo. Usando [proprietà](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) per incapsulare il campo, è possibile impedire l'accesso diretto ai campi.  
  
 Per creare la nuova proprietà, il **Incapsula campo** operazione cambia il modificatore di accesso per il campo che si vuole incapsulare su [privato](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8), quindi genera [ottenere](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)e [impostare](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) funzioni di accesso per tale campo. In alcuni casi, viene generata una sola funzione di accesso `get`, ad esempio quando il campo viene dichiarato di sola lettura.  
  
 Il motore di refactoring di aggiornare il codice con riferimenti nella nuova proprietà nelle aree specificate nel **aggiornare i riferimenti** sezione del **Incapsula campo** nella finestra di dialogo.  
  
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
  
2.  Nel [Editor di codice](../ide/writing-code-in-the-code-and-text-editor.md), posizionare il cursore nella dichiarazione, sul nome del campo che si vuole incapsulare. Nell'esempio seguente, posizionare il cursore sulla parola `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  Nel **refactoring** menu, fare clic su **Incapsula campo**.  
  
     Il **Incapsula campo** verrà visualizzata la finestra di dialogo.  
  
     È anche possibile premere il tasto di scelta rapida CTRL + R, E per visualizzare il **Incapsula campo** nella finestra di dialogo.  
  
     È anche possibile fare doppio clic sul cursore, scegliere **refactoring**e quindi fare clic su **Incapsula campo** per visualizzare il **Incapsula campo** nella finestra di dialogo.  
  
4.  Specificare le impostazioni.  
  
5.  Premere INVIO oppure fare clic sui **OK** pulsante.  
  
6.  Se è stata selezionata la **Anteprima modifiche riferimento** opzione, il **Anteprima modifiche riferimento** verrà visualizzata la finestra. Scegliere il **applica** pulsante.  
  
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
  
 Per più campi, le dichiarazioni relative **Incapsula campo** utilizza la virgola come limite tra i campi e avvia il refactoring nel campo più vicino al cursore e sulla stessa riga del cursore. È inoltre possibile specificare il campo che si desidera incapsulare selezionandone il nome nella dichiarazione.  
  
 Il codice generato da questa operazione di refactoring viene modellato dalla funzionalità di frammenti di codice per Incapsula campo. I frammenti di codice sono modificabili. Per altre informazioni, vedere [Code Snippets](../ide/code-snippets.md) (Frammenti di codice).  
  
## <a name="see-also"></a>Vedere anche  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)   
 [Frammenti di codice Visual C#](../ide/visual-csharp-code-snippets.md)