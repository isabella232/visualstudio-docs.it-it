---
title: 'Procedura dettagliata: Creazione di una web part per SharePoint | Microsoft Docs'
description: Creare una web part per SharePoint. Le web part consentono agli utenti di modificare direttamente il contenuto, l'aspetto e il comportamento SharePoint pagine del sito tramite un browser.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9bdeb3397c3c958912010af9f822b48a66add8e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123281"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Procedura dettagliata: Creare una web part per SharePoint

Web part consentire agli utenti di modificare direttamente il contenuto, l'aspetto e il comportamento SharePoint pagine del sito tramite un browser. Questa procedura dettagliata illustra come creare una web part usando il modello di elemento **web part** in Visual Studio 2010.

La web part visualizza i dipendenti in una griglia dei dati. L'utente specifica il percorso del file che contiene i dati dei dipendenti. L'utente può anche filtrare la griglia dei dati in modo che i dipendenti responsabili vengano visualizzati solo nell'elenco.

Vengono illustrate le attività seguenti:

- Creazione di una web part usando il modello Visual Studio **elemento web part.**

- Creazione di una proprietà che può essere impostata dall'utente della web part. Questa proprietà specifica il percorso del file di dati dei dipendenti.

- Rendering del contenuto in una web part mediante l'aggiunta di controlli alla raccolta di controlli Web part.

- Creazione di una nuova voce di menu, definita *verbo,* visualizzata nel menu dei verbi della web part sottoposta a rendering. I verbi consentono all'utente di modificare i dati visualizzati nella web part.

- Test della web part in SharePoint.

    > [!NOTE]
    > Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio 2017 o Azure DevOps Services.

## <a name="create-an-empty-sharepoint-project"></a>Creare un progetto SharePoint vuoto

Creare prima di tutto un progetto SharePoint vuoto. Successivamente, si aggiungerà una web part al progetto usando il **modello di elemento Web part.**

1. Iniziare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando **l'opzione Esegui come** amministratore.

2. Nella barra degli uomini scegliere **File**  >  **nuovo**  >  **Project**.

3. Nella **finestra di dialogo Nuovo** Project  espandere il nodo SharePoint sotto il linguaggio che si vuole usare e quindi scegliere il **nodo 2010.**

4. Nel riquadro **Modelli** scegliere SharePoint **2010 Project** e quindi fare clic sul **pulsante OK.**

     Verrà **SharePoint personalizzazione guidata.** Questa procedura guidata consente di selezionare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.

5. Scegliere il **pulsante di opzione** Distribuisci come  soluzione farm e quindi scegliere il pulsante Fine per accettare il sito locale SharePoint predefinito.

## <a name="add-a-web-part-to-the-project"></a>Aggiungere una web part al progetto

Aggiungere un **elemento web part** al progetto. **L'elemento Web part** aggiunge il file di codice della web part. Successivamente, si aggiungerà codice al file di codice della web part per eseguire il rendering del contenuto della web part.

1. Sulla barra dei menu **scegliere** Project Aggiungi nuovo  >  **elemento**.

2. Nel **riquadro** Modelli installati della  finestra di dialogo **Aggiungi** nuovo elemento espandere il nodo SharePoint e quindi scegliere il **nodo 2010.**

3. Nell'elenco dei SharePoint modelli scegliere il **modello web part** e quindi scegliere il **pulsante** Aggiungi.

     **L'elemento web part** viene visualizzato in **Esplora soluzioni**.

## <a name="rendering-content-in-the-web-part"></a>Rendering del contenuto nella web part

È possibile specificare i controlli da visualizzare nella web part aggiungendoli alla raccolta di controlli della classe web part.

1. In **Esplora soluzioni** aprire *WebPart1.vb* (in Visual Basic) o *WebPart1.cs* (in C#).

     Il file di codice della web part viene aperto nell'editor di codice.

2. Aggiungere le direttive seguenti all'inizio del file di codice della web part.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet1":::

3. Aggiungere il codice seguente alla classe `WebPart1` . Questo codice dichiara i campi seguenti:

   - Griglia di dati per visualizzare i dipendenti nella web part.

   - Testo visualizzato nel controllo utilizzato per filtrare la griglia dei dati.

   - Etichetta che visualizza un errore se la griglia dei dati non è in grado di visualizzare i dati.

   - Stringa contenente il percorso del file di dati del dipendente.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet2":::

4. Aggiungere il codice seguente alla classe `WebPart1` . Questo codice aggiunge una proprietà personalizzata `DataFilePath` denominata alla web part. Una proprietà personalizzata è una proprietà che può essere impostata in SharePoint dall'utente. Questa proprietà ottiene e imposta il percorso di un file di dati XML utilizzato per popolare la griglia dei dati.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet3":::

5. Sostituire il metodo `CreateChildControls` con il codice seguente. Il codice esegue queste operazioni:

   - Aggiunge la griglia dei dati e l'etichetta dichiarate nel passaggio precedente.

   - Associa la griglia dei dati a un file XML che contiene i dati dei dipendenti.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet4":::

6. Aggiungi alla classe `WebPart1` il metodo seguente. Il codice esegue queste operazioni:

   - Crea un verbo visualizzato nel menu dei verbi della web part sottoposta a rendering.

   - Gestione dell'evento generato quando l'utente sceglie il verbo nel relativo menu. Questo codice filtra l'elenco di dipendenti visualizzato nella griglia dei dati.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet5":::

## <a name="test-the-web-part"></a>Testare la web part

Quando si esegue il progetto, viene aperto SharePoint sito web. La web part viene aggiunta automaticamente alla raccolta di web part in SharePoint. È possibile aggiungere la web part a qualsiasi pagina web part.

1. Incollare il codice XML seguente in un Blocco note file. Questo file XML contiene i dati di esempio che verranno visualizzati nella web part.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. Nella Blocco note menu scegliere **Salva** con nome dalla barra  >  **dei** menu.

3. **Nell'elenco Tipo** file della finestra di dialogo Salva **con** nome scegliere Tutti **i file**.

4. Nella casella **Nome file** immettere **data.xml**.

5. Scegliere una cartella qualsiasi usando il **pulsante Sfoglia** cartelle e quindi scegliere **il pulsante** Salva.

6. In Visual Studio premere **F5.**

     Verrà SharePoint sito di lavoro.

7. Scegliere **Altre** opzioni dal menu Azioni **sito**.

8. Nella pagina **Crea** scegliere il **tipo di pagina web part,** quindi scegliere **il pulsante** Crea.

9. Nella pagina **Nuova pagina web part** assegnare alla pagina il nome **SampleWebPartPage.aspx** e quindi scegliere **il pulsante** Crea.

     Verrà visualizzata la pagina web part.

10. Selezionare qualsiasi area nella pagina web part.

11. Nella parte superiore della pagina scegliere la **scheda** Inserisci e quindi scegliere il **pulsante Web** part.

12. Nel riquadro **Categorie** scegliere la **cartella Personalizzata,** scegliere la **web part WebPart1** e quindi scegliere **il pulsante** Aggiungi.

     La web part viene visualizzata nella pagina.

## <a name="test-the-custom-property"></a>Testare la proprietà personalizzata

Per popolare la griglia dei dati visualizzata nella web part, specificare il percorso del file XML contenente i dati relativi a ogni dipendente.

1. Scegliere la freccia visualizzata sul lato destro della web part e quindi scegliere Modifica **web part** dal menu visualizzato.

     Sul lato destro della pagina viene visualizzato un riquadro contenente le proprietà per la web part.

2. Nel riquadro espandere  il nodo Varie, immettere il percorso del file XML creato in precedenza, scegliere il **pulsante** Applica e quindi scegliere **OK.**

     Verificare che nella web part sia visualizzato un elenco di dipendenti.

## <a name="test-the-web-part-verb"></a>Testare il verbo web part

Visualizzare e nascondere i dipendenti che non sono responsabili selezionando un elemento visualizzato nel menu dei verbi della web part.

1. Scegliere la freccia visualizzata sul lato destro della web part e quindi scegliere **Mostra** solo manager dal menu visualizzato.

     Nella web part vengono visualizzati solo i dipendenti responsabili.

2. Scegliere di nuovo la freccia e quindi **scegliere Mostra** tutti i dipendenti dal menu visualizzato.

     Tutti i dipendenti vengono visualizzati nella web part.

## <a name="see-also"></a>Vedi anche

[Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Procedura: Creare una SharePoint web part](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Procedura: Creare una SharePoint web part usando una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 [Procedura dettagliata: Creare una web part per SharePoint usando una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
