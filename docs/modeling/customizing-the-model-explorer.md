---
title: Personalizzazione di Esplora modelli
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96c12ac2063e6b3ac04e3c0e9b0c20c69ea91a35
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589708"
---
# <a name="customizing-the-model-explorer"></a>Personalizzazione di Esplora modelli
È possibile modificare l'aspetto e il comportamento di Esplora risorse per la finestra di progettazione del linguaggio specifico di dominio come indicato di seguito:

- Modificare il titolo della finestra.

- Modificare l'icona della scheda.

- Modificare le icone per i nodi.

- Nascondere i nodi.

## <a name="changing-the-window-title"></a>Modifica del titolo della finestra
 Per modificare il titolo della finestra di Esplora generato, selezionare **comportamento di Esplora risorse** in **Esplora DSL**, quindi nella finestra **proprietà** impostare la proprietà **title** sul titolo desiderato.

## <a name="changing-the-tab-icon"></a>Modifica dell'icona della scheda
 Per modificare l'icona della scheda per Esplora risorse, usare un'icona 16x16-pixel in un file con estensione bmp. Inserire il file dell'icona nella cartella \DslPackage\Resources\, quindi modificare il nome del file in **ModelExplorerToolWindowBitmaps. bmp**. Ad esempio, è possibile modificare il file dell'icona Setup. ico di Visual Studio in formato BMP e rinominarlo **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. La finestra di progettazione generata visualizzerà questa icona nella scheda della finestra di esplorazione quando viene ancorata insieme a **Esplora soluzioni**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Impostazione delle icone personalizzate nei nodi di esplorazione
 È possibile personalizzare i nodi in Esplora risorse usando le impostazioni del nodo di esplorazione. Nella procedura seguente viene illustrato come aggiungere un'icona a un nodo.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Per aggiungere un'icona a un nodo di esplorazione

1. Creare una soluzione [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usando il modello di soluzione flusso attività.

2. Inserire un file con estensione BMP contenente un'icona 16x16-pixel nella cartella **Dsl\Resources** della soluzione.

3. In **DSL Explorer**fare clic con il pulsante destro del mouse su **Esplora comportamento** e quindi scegliere **Aggiungi nuove impostazioni del nodo di esplorazione**.

    Viene visualizzato un nodo **ExplorerNodeSettings** sotto il nodo **Impostazioni nodo personalizzato** .

4. Selezionare **ExplorerNodeSettings**, quindi nella finestra **Proprietà** impostare **Class** su **Actor**.

5. Impostare l' **icona per visualizzare** il percorso del file icona.

6. Trasformare tutti i modelli, quindi compilare ed eseguire la soluzione.

7. Nella finestra di progettazione generata aprire il diagramma di esempio.

    La finestra di esplorazione dovrebbe mostrare tre nodi **Actor** con l'icona.

> [!NOTE]
> Se è stata impostata un'icona di nodo per qualsiasi elemento visualizzato nell'esploratore generato, l'icona verrà visualizzata in tutti i nodi di esplorazione. Se non è stata impostata alcuna icona, nei nodi viene visualizzata l'icona predefinita.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Modifica del nome visualizzato in un nodo di esplorazione
 È possibile modificare la modalità di visualizzazione dei nomi degli elementi del modello in Esplora. Nella procedura riportata di seguito viene illustrato come visualizzare il nome dell' **attività** a cui fa riferimento un **Commento** nel nodo Comment.

#### <a name="to-display-a-property"></a>Per visualizzare una proprietà

1. Aprire la soluzione creata nella procedura precedente.

2. Verificare che il **Commento** faccia riferimento solo a una singola classe di dominio impostando la molteplicità del ruolo con gli **oggetti** nome proprietà su 0.. 1. Il nome della proprietà deve essere **soggetto**e il nome della relazione deve diventare **CommentReferencesSubject**.

3. In **DSL Explorer**fare clic con il pulsante destro del mouse su **Esplora comportamento** e quindi scegliere **Aggiungi nuove impostazioni del nodo di esplorazione**.

     Viene visualizzato un nodo **ExplorerNodeSettings** sotto il nodo **Impostazioni nodo personalizzato** .

4. Selezionare **ExplorerNodeSettings**, quindi nella finestra **Proprietà** impostare **Class** su **Comment**.

5. Fare clic con il pulsante destro del mouse sul nodo **Comment** , quindi scegliere **Aggiungi nuovo percorso proprietà**.

     Viene visualizzato un nuovo nodo denominato **Proprietà**denominata.

6. Selezionare **Proprietà visualizzata**, quindi nella finestra **Proprietà** fare clic sul campo valore di percorso della **proprietà**. Selezionare **Comment**, quindi **CommentReferencesSubject**e **FlowElement**. Il percorso risultante sarà simile a **CommentReferencesSubject. Subject/! Oggetto**.

7. Nel campo valore della **Proprietà**selezionare **nome**.

8. Trasformare tutti i modelli, quindi compilare ed eseguire la soluzione.

9. Nella finestra di progettazione generata aprire il diagramma di esempio.

10. Disegno di un **connettore di commenti** tra l'elemento Comment e l'elemento **Task1** nel diagramma.

     Il nodo Explorer dovrebbe visualizzare il commento come **Task1**.

## <a name="hiding-nodes"></a>Nascondere nodi
 È possibile nascondere un nodo in Esplora risorse aggiungendo il relativo percorso al nodo **nodi nascosti** di **Esplora DSL**. Nella procedura seguente viene illustrato come nascondere i nodi di **Commento** .

#### <a name="to-hide-an-explorer-node"></a>Per nascondere un nodo di esplorazione

1. Aprire la soluzione creata nella procedura precedente.

2. In **DSL Explorer**fare clic con il pulsante destro del mouse su **Esplora comportamento** , quindi scegliere **Aggiungi nuovo percorso di dominio**.

     Un nodo del **percorso di dominio** viene visualizzato sotto i **nodi nascosti**.

3. Selezionare **percorso dominio**, quindi nella finestra **Proprietà** fare clic sul campo valore di **definizione percorso**. Selezionare **FlowGraph**, quindi **FlowGraphHasComments**. Il percorso risultante sarà simile a **FlowGraphHasComments. comments**

4. Trasformare tutti i modelli, quindi compilare ed eseguire la soluzione.

5. Nella finestra di progettazione generata aprire il diagramma di esempio.

     La finestra di esplorazione dovrebbe visualizzare solo un nodo **Actors** e non deve visualizzare il nodo **Commenti** .

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
