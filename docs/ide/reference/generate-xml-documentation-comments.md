---
title: Inserire commenti relativi alla documentazione XML
description: Informazioni su come inserire commenti relativi alla documentazione XML nel codice che è possibile usare per creare un file XML generato dal compilatore da distribuire insieme all'assembly .NET.
ms.custom: SEO-VS-2020
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 5b538fe8b9f9ab61486f49efb33fac56356ae1c2ffdd9051e39687696c392b62
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357414"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Procedura: Inserire commenti XML per la generazione di documentazione

Visual Studio consente di documentare gli elementi del codice, ad esempio classi e metodi, generando automaticamente la struttura standard per i commenti in formato documentazione XML. In fase di compilazione, è possibile generare un file XML che contiene i commenti in formato di documentazione.

> [!TIP]
> Per informazioni sulla configurazione di nome e percorso del file XML generato, vedere [Documentazione del codice con i commenti XML (Guida per C#)](/dotnet/csharp/codedoc).

Il file XML generato dal compilatore può essere distribuito insieme agli assembly .NET in modo che Visual Studio e altri IDE possano usare IntelliSense per visualizzare informazioni rapide su tipi e membri. È anche possibile eseguire il file XML tramite strumenti, ad esempio [DocFX](https://dotnet.github.io/docfx/) e [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) per generare i siti Web di riferimento all'API.

> [!NOTE]
> Il comando **Inserisci commento** per inserire automaticamente i commenti in formato documentazione XML è disponibile in [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) e [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). È comunque possibile inserire manualmente [commenti in formato documentazione XML in file C++](/cpp/build/reference/xml-documentation-visual-cpp) e generare file di documentazione XML in fase di compilazione.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Per inserire commenti XML per un elemento di codice

1. Posizionare il cursore del testo sopra l'elemento da documentare, ad esempio, un metodo.

2. Eseguire una delle operazioni seguenti:

   - Digitare `///` in C# o `'''` in Visual Basic

   - Dal menu **Modifica** scegliere **IntelliSense** > **Inserisci commento**

   - Dal menu di scelta rapida o dal menu di scelta rapida nell'elemento di codice o sopra l'elemento di codice scegliere **Inserisci**  >  **commento frammento**

   Il modello XML viene generato subito sopra l'elemento di codice. Ad esempio, quando si imposta come commento un metodo, vengono generati l'elemento , un elemento per ogni parametro e un elemento per **\<summary\>** **\<param\>** **\<returns\>** documentare il valore restituito.

   ![Modello di commento XML - C#](media/doc-preview-cs.png)

   ![Modello di commento XML - Visual Basic](media/doc-preview-vb.png)

3. Immettere descrizioni per ogni elemento XML per documentare in modo completo l'elemento di codice.

   ![Screenshot che mostra il commento completato.](media/doc-result-cs.png)

È possibile usare gli stili nei commenti XML di cui verrà eseguito il rendering in Informazioni rapide quando si passa il mouse sull'elemento. Questi stili includono corsivo, grassetto, punti elenco e un collegamento selezionabile.

   ![Screenshot che mostra il commento completato con tag di stile per corsivo, grassetto, punti elenco e un collegamento selezionabile.](media/doc-style-cs.png) 

> [!NOTE]
> È disponibile un'[opzione](../../ide/reference/options-text-editor-csharp-advanced.md) per attivare/disattivare i commenti in formato documentazione XML dopo aver digitato `///` in C# o `'''` in Visual Basic. Dalla barra dei menu scegliere Opzioni  >  **strumenti per** aprire la finestra di **dialogo** Opzioni. Passare quindi a Editor **di testo**  >  **C#** o Avanzate **di**  >  **base.** Nella sezione **Guida editor** cercare l'opzione **Genera commenti relativi alla documentazione XML**.

## <a name="see-also"></a>Vedi anche

- [Commenti relativi alla documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentazione del codice con i commenti XML (Guida per C#)](/dotnet/csharp/codedoc)
- [Procedura: Creare documentazione XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Commenti C++](/cpp/cpp/comments-cpp)
- [Documentazione XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generazione codice](../code-generation-in-visual-studio.md)
