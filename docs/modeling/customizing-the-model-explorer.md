---
title: Personalizzazione di Esplora modelli
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9127531c81471c7ae1bba58224c4d206a0be9c50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039098"
---
# <a name="customizing-the-model-explorer"></a>Personalizzazione di Esplora modelli
È possibile modificare l'aspetto e il comportamento di esplorazione per la finestra di progettazione di linguaggio specifico di dominio come indicato di seguito:

-   Modificare il titolo della finestra.

-   Modificare l'icona di scheda.

-   Modificare le icone per i nodi.

-   Nascondere i nodi.

## <a name="changing-the-window-title"></a>Modificare il titolo della finestra
 Per modificare il titolo della finestra di Esplora generato, selezionare **comportamento di esplorazione** nel **DSL Explorer**e quindi nel **proprietà** impostare nella finestra di  **Titolo** proprietà per il titolo desiderato.

## <a name="changing-the-tab-icon"></a>Modifica dell'icona di scheda
 Per modificare l'icona di scheda per Esplora risorse, usare un'icona di 16x16 pixel in un file con estensione bmp. Inserire il file icona nella cartella \DslPackage\Resources\ e quindi modificare il nome del file per **ModelExplorerToolWindowBitmaps.bmp**. Ad esempio, è possibile modificare il file dell'icona setup.ico Visual Studio in formato BMP e rinominarlo **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Finestra di progettazione generata verrà visualizzata questa icona nella scheda della finestra Esplora risorse quando è ancorata assieme **Esplora soluzioni**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Impostazione delle icone personalizzate nei nodi di Esplora
 È possibile personalizzare i nodi in Esplora risorse con impostazioni nodo di esplorazione. La procedura seguente viene illustrato come aggiungere un'icona per un nodo.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Per aggiungere un'icona per un nodo di esplorazione

1. Creare un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione usando il modello di soluzione flusso attività.

2. Inserire un file con estensione bmp contiene un'icona di 16x16 pixel nel **Dsl\Resources** cartella della soluzione.

3. Nel **DSL Explorer**, fare doppio clic su **comportamento di esplorazione** e quindi fare clic su **aggiungere nuove impostazioni di Esplora nodo**.

    Un' **ExplorerNodeSettings** nodo viene visualizzato sotto il **impostazioni personalizzate nodo** nodo.

4. Selezionare **ExplorerNodeSettings**, quindi nel **delle proprietà** impostare nella finestra **classe** per **attore**.

5. Impostare **alla visualizzazione dell'icona** al percorso del file icona.

6. Trasforma tutti i modelli e quindi compilare ed eseguire la soluzione.

7. Nella finestra di progettazione generata, aprire il diagramma di esempio.

    Esplora risorse dovrebbe mostrare tre **attore** nodi che dispongono dell'icona.

> [!NOTE]
>  Se è stata impostata un'icona di nodo per qualsiasi elemento che viene visualizzato in Esplora generato, tutti i nodi di Esplora verranno visualizzata l'icona. Se non è stata impostata alcuna icona, i nodi visualizzerà l'icona predefinita.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>La modifica del nome visualizzato su un nodo di Esplora
 È possibile modificare la modalità in cui vengono visualizzati i nomi degli elementi del modello in Esplora risorse. La procedura seguente viene illustrato come visualizzare il nome del **Task** che fa riferimento un **commento** nel nodo di commento.

#### <a name="to-display-a-property"></a>Per visualizzare una proprietà

1.  Aprire la soluzione creata nella procedura precedente.

2.  Assicurarsi che il **commento** fa riferimento solo una classe di dominio singolo, impostare la molteplicità del ruolo con nome della proprietà **soggetti** a 0..1. Il nome della proprietà deve diventare **Subject**, il nome della relazione deve diventare **CommentReferencesSubject**.

3.  Nel **DSL Explorer**, fare doppio clic su **comportamento di esplorazione** e quindi fare clic su **aggiungere nuove impostazioni di Esplora nodo**.

     Un' **ExplorerNodeSettings** nodo viene visualizzato sotto il **impostazioni personalizzate nodo** nodo.

4.  Selezionare **ExplorerNodeSettings**, quindi nel **delle proprietà** impostare nella finestra **classe** a **commento**.

5.  Fare doppio clic il **commento** nodo e quindi fare clic su **aggiunta nuovo percorso di proprietà**.

     Verrà visualizzato un nuovo nodo denominato **proprietà visualizzata**.

6.  Selezionare **proprietà visualizzata**e quindi la **proprietà** finestra, fare clic sul campo del valore **percorso alla proprietà**. Selezionare **commento**, quindi **CommentReferencesSubject**, quindi **FlowElement**. Il percorso risulta dovrebbe essere simile **CommentReferencesSubject.Subject/! Soggetto**.

7.  Nel campo del valore **proprietà**, selezionare **nome**.

8.  Trasforma tutti i modelli e quindi compilare ed eseguire la soluzione.

9. Nella finestra di progettazione generata, aprire il diagramma di esempio.

10. Disegnare una **connettore di commento** tra l'elemento di commento e il **Attività1** elemento del diagramma.

     Il nodo di esplorazione deve visualizzare il commento come **Attività1**.

## <a name="hiding-nodes"></a>Nodi di occultamento
 È possibile nascondere un nodo in Esplora risorse aggiungendo il percorso per il **i nodi nascosti** nodo del **DSL Explorer**. La procedura seguente illustra come nascondere **commento** nodi.

#### <a name="to-hide-an-explorer-node"></a>Per nascondere un nodo di esplorazione

1.  Aprire la soluzione creata nella procedura precedente.

2.  Nel **DSL Explorer**, fare doppio clic su **comportamento di esplorazione** e quindi fare clic su **aggiunta nuovo percorso di dominio**.

     Oggetto **percorso di dominio** nodo viene visualizzato sotto **nodi nascosti**.

3.  Selezionare **percorso di dominio**, quindi nel **proprietà** finestra, fare clic sul campo del valore **percorso definizione**. Selezionare **FlowGraph**, quindi **FlowGraphHasComments**. Il percorso risulta dovrebbe essere simile **FlowGraphHasComments.Comments**

4.  Trasforma tutti i modelli e quindi compilare ed eseguire la soluzione.

5.  Nella finestra di progettazione generata, aprire il diagramma di esempio.

     Finestra di esplorazione deve mostrare solo un' **attori** nodo e non deve visualizzare il **commenti** nodo.

## <a name="see-also"></a>Vedere anche

- [Glossario sugli strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)