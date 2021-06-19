---
title: Personalizzazione di Esplora modelli
description: Informazioni su come modificare l'aspetto e il comportamento dello explorer per la finestra di progettazione del linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c842988f3e5c9f1bbed5a859e73680cb109ecd43
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385903"
---
# <a name="customizing-the-model-explorer"></a>Personalizzazione di Esplora modelli
È possibile modificare l'aspetto e il comportamento dello explorer per la finestra di progettazione del linguaggio specifico di dominio come indicato di seguito:

- Modificare il titolo della finestra.

- Modificare l'icona della scheda.

- Modificare le icone per i nodi.

- Nascondere i nodi.

## <a name="changing-the-window-title"></a>Modifica del titolo della finestra
 Per modificare il titolo della finestra di esplorazione generata, selezionare Comportamento esplora  risorse **in** **Esplora DSL** e quindi nella finestra Proprietà impostare la proprietà **Titolo** sul titolo desiderato.

## <a name="changing-the-tab-icon"></a>Modifica dell'icona della scheda
 Per modificare l'icona della scheda per lo strumento di esplorazione, usare un'icona di 16x16 pixel in un file .bmp. Inserire il file dell'icona nella cartella \DslPackage\Resources\ e quindi modificare il nome del file **ModelExplorerToolWindowBitmaps.bmp**. Ad esempio, è possibile modificare il file Visual Studio icona setup.ico in .bmp e rinominarlo **inDSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. La finestra di progettazione generata visualizza questa icona nella scheda dello explorer quando è ancorata insieme a **Esplora soluzioni**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Impostazione di icone personalizzate nei nodi di Explorer
 È possibile personalizzare i nodi nello strumento di esplorazione usando le impostazioni dei nodi di Esplora risorse. La procedura seguente illustra come aggiungere un'icona a un nodo.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Per aggiungere un'icona a un nodo di esplorazione

1. Creare una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione usando il modello di soluzione Flusso attività.

2. Inserire un .bmp file contenente un'icona di 16x16 pixel nella cartella **Dsl\Resources** della soluzione.

3. In Esplora **DSL fare** clic con il pulsante destro **del mouse** su Comportamento esplora risorse e quindi scegliere Aggiungi nuove impostazioni nodo **Esplora** risorse .

    Nel nodo Impostazioni nodo personalizzate viene visualizzato un **nodo** **ExplorerNodeSettings.**

4. Selezionare **ExplorerNodeSettings** e quindi nella **finestra Proprietà** impostare **Classe** su **Actor.**

5. Impostare **Icona da visualizzare** sul percorso del file dell'icona.

6. Trasformare tutti i modelli, quindi compilare ed eseguire la soluzione.

7. Nella finestra di progettazione generata aprire il diagramma di esempio.

    In Esplora risorse dovrebbero essere visualizzati **tre nodi Actor** con l'icona.

> [!NOTE]
> Se è stata impostata un'icona del nodo per qualsiasi elemento visualizzato nell'explorer generato, tutti i nodi di esplorazione visualizzano l'icona. Se non è stata impostata alcuna icona, i nodi visualizzano l'icona predefinita.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Modifica del nome visualizzato in un nodo di Esplora risorse
 È possibile modificare la modalità di visualizzazione dei nomi degli elementi del modello nella finestra di esplorazione. Nella procedura seguente viene illustrato come visualizzare il nome **dell'attività** a cui fa riferimento **un commento** nel nodo commento.

#### <a name="to-display-a-property"></a>Per visualizzare una proprietà

1. Aprire la soluzione creata nella procedura precedente.

2. Assicurarsi che il **commento** faccia riferimento solo a una singola classe di dominio impostando la molteplicità del ruolo con il nome di proprietà **Soggetti** su 0..1. Il nome della proprietà deve diventare **Subject** e il nome della relazione deve diventare **CommentReferencesSubject.**

3. In Esplora **DSL fare** clic con il pulsante destro **del mouse** su Comportamento esplora risorse e quindi scegliere Aggiungi nuove impostazioni nodo **Esplora** risorse .

     Nel nodo Impostazioni nodo personalizzate viene visualizzato un **nodo** **ExplorerNodeSettings.**

4. Selezionare **ExplorerNodeSettings** e quindi nella **finestra Proprietà** impostare **Classe** su **Commento.**

5. Fare clic con il pulsante destro **del mouse** sul nodo Commento e quindi scegliere Aggiungi nuovo **percorso proprietà**.

     Viene visualizzato un nuovo nodo denominato **Proprietà visualizzata**.

6. Selezionare **Proprietà visualizzata** e quindi nella finestra **Proprietà** fare clic sul campo del valore di **Percorso proprietà**. Selezionare **Comment**(Commento), **CommentReferencesSubject (Commenti** Sottosoggetti), quindi **FlowElement**. Il percorso risultante dovrebbe essere simile **a CommentReferencesSubject.Subject/! Oggetto**.

7. Nel campo del valore di **Proprietà** selezionare **Nome**.

8. Trasformare tutti i modelli e quindi compilare ed eseguire la soluzione.

9. Nella finestra di progettazione generata aprire il diagramma di esempio.

10. Disegnare un **connettore di** commenti tra l'elemento comment e **l'elemento Task1** nel diagramma.

     Il nodo Explorer dovrebbe visualizzare il commento **Task1.**

## <a name="hiding-nodes"></a>Nascondere i nodi
 È possibile nascondere un nodo nella finestra di esplorazione aggiungendone il percorso al **nodo Nodi** nascosti di **DSL Explorer.** La procedura seguente illustra come nascondere i **nodi Comment.**

#### <a name="to-hide-an-explorer-node"></a>Per nascondere un nodo di esplorazione

1. Aprire la soluzione creata nella procedura precedente.

2. In **Esplora DSL fare** clic con il pulsante destro **del mouse** su Comportamento esplora risorse e quindi scegliere Aggiungi nuovo **percorso dominio**.

     In **Nodi nascosti viene** visualizzato un nodo Percorso **dominio**.

3. Selezionare **Percorso dominio** e quindi nella finestra **Proprietà** fare clic sul campo del valore di Definizione **percorso**. Selezionare **FlowGraph** e quindi **FlowGraphHasComments.** Il percorso risultante dovrebbe essere simile **a FlowGraphHasComments.Comments**

4. Trasformare tutti i modelli e quindi compilare ed eseguire la soluzione.

5. Nella finestra di progettazione generata aprire il diagramma di esempio.

     La finestra di esplorazione dovrebbe mostrare solo un **nodo Actors** e non il **nodo** Commenti.

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))