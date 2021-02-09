---
title: 'Procedura dettagliata: creazione di una Web part per SharePoint | Microsoft Docs'
description: Creare una Web part per SharePoint. Le web part consentono agli utenti di modificare direttamente il contenuto, l'aspetto e il comportamento delle pagine del sito di SharePoint tramite un browser.
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
ms.workload:
- office
ms.openlocfilehash: 0f2d14bfd069fcf5064c9d8643393e28e52570be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918635"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Procedura dettagliata: creare una Web part per SharePoint

Web part consentire agli utenti di modificare direttamente il contenuto, l'aspetto e il comportamento delle pagine del sito di SharePoint tramite un browser. In questa procedura dettagliata viene illustrato come creare una Web part tramite il modello di elemento **Web part** in Visual Studio 2010.

La Web part Visualizza i dipendenti in una griglia di dati. L'utente specifica il percorso del file che contiene i dati del dipendente. L'utente può inoltre filtrare la griglia dei dati in modo che i dipendenti responsabili siano visualizzati solo nell'elenco.

Vengono illustrate le attività seguenti:

- Creazione di una Web part tramite il modello di elemento **Web part** di Visual Studio.

- Creazione di una proprietà che può essere impostata dall'utente della web part. Questa proprietà specifica il percorso del file di dati del dipendente.

- Rendering del contenuto in una Web part mediante l'aggiunta di controlli alla raccolta di controlli Web part.

- Creazione di una nuova voce di menu, denominata *verbo,* che viene visualizzata nel menu dei verbi della web part di cui è stato eseguito il rendering. I verbi consentono all'utente di modificare i dati visualizzati nella web part.

- Test della web part in SharePoint.

    > [!NOTE]
    > Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio 2017 o Azure DevOps Services.

## <a name="create-an-empty-sharepoint-project"></a>Creazione di un progetto SharePoint vuoto

Per prima cosa, creare un progetto SharePoint vuoto. Successivamente, sarà necessario aggiungere una Web part al progetto utilizzando il modello di elemento **Web part** .

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Per iniziare, usare l'opzione **Esegui come amministratore** .

2. Sulla barra degli uomini scegliere **file**  >  **nuovo**  >  **progetto**.

3. Nella finestra di dialogo **nuovo progetto** espandere il nodo **SharePoint** sotto la lingua che si desidera utilizzare, quindi scegliere il nodo **2010** .

4. Nel riquadro **modelli** scegliere **progetto SharePoint 2010**, quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** . Questa procedura guidata consente di selezionare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.

5. Scegliere il pulsante di opzione **Distribuisci come soluzione farm** , quindi scegliere il pulsante **fine** per accettare il sito di SharePoint locale predefinito.

## <a name="add-a-web-part-to-the-project"></a>Aggiungere una Web part al progetto

Aggiungere un elemento **Web part** al progetto. L'elemento **Web part** aggiunge il file di codice della web part. Successivamente, si aggiungerà codice al file di codice della web part per eseguire il rendering del contenuto della web part.

1. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

2. Nel riquadro **modelli installati** della finestra di dialogo **Aggiungi nuovo elemento** espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

3. Nell'elenco dei modelli di SharePoint scegliere il modello **Web part** , quindi scegliere il pulsante **Aggiungi** .

     L'elemento **Web part** viene visualizzato in **Esplora soluzioni**.

## <a name="rendering-content-in-the-web-part"></a>Rendering del contenuto nella web part

È possibile specificare i controlli che si desidera visualizzare nella web part aggiungendoli alla raccolta di controlli della classe Web part.

1. In **Esplora soluzioni** aprire *WebPart1. vb* (in Visual Basic) o *WebPart1.cs* (in C#).

     Il file di codice della web part verrà aperto nell'editor di codice.

2. Aggiungere le seguenti direttive all'inizio del file di codice della web part.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Aggiungere il codice seguente alla classe `WebPart1` . Questo codice dichiara i campi seguenti:

   - Griglia di dati per visualizzare i dipendenti nella web part.

   - Testo visualizzato sul controllo usato per filtrare la griglia dei dati.

   - Etichetta che visualizza un errore se la griglia dati non è in grado di visualizzare i dati.

   - Stringa che contiene il percorso del file di dati del dipendente.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Aggiungere il codice seguente alla classe `WebPart1` . Questo codice aggiunge una proprietà personalizzata denominata `DataFilePath` alla web part. Una proprietà personalizzata è una proprietà che può essere impostata in SharePoint dall'utente. Questa proprietà ottiene e imposta il percorso di un file di dati XML utilizzato per popolare la griglia dei dati.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Sostituire il metodo `CreateChildControls` con il codice seguente. Il codice esegue queste operazioni:

   - Aggiunge la griglia di dati e l'etichetta dichiarata nel passaggio precedente.

   - Associa la griglia dati a un file XML che contiene i dati del dipendente.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Aggiungi alla classe `WebPart1` il metodo seguente. Il codice esegue queste operazioni:

   - Consente di creare un verbo visualizzato nel menu dei verbi della web part della web part di cui è stato eseguito il rendering.

   - Gestione dell'evento generato quando l'utente sceglie il verbo nel relativo menu. Questo codice filtra l'elenco dei dipendenti visualizzati nella griglia dei dati.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Testare la Web part

Quando si esegue il progetto, viene aperto il sito di SharePoint. La Web part viene aggiunta automaticamente alla raccolta di Web part in SharePoint. È possibile aggiungere la Web part a qualsiasi pagina Web part.

1. Incollare il codice XML seguente in un file del blocco note. Il file XML contiene i dati di esempio che verranno visualizzati nella web part.

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

2. Nella barra dei menu del blocco note scegliere **file**  >  **Salva con nome**.

3. Nella finestra di dialogo **Salva con nome** selezionare **tutti i file** nell'elenco **Salva come** .

4. Nella casella **nome file** immettere **data.xml**.

5. Scegliere una cartella qualsiasi tramite il pulsante **Sfoglia cartelle** , quindi scegliere il pulsante **Salva** .

6. In Visual Studio premere il tasto **F5** .

     Verrà aperto il sito di SharePoint.

7. Scegliere **altre opzioni** dal menu **Azioni sito** .

8. Nella pagina **Crea** scegliere il tipo di **pagina Web part** , quindi scegliere il pulsante **Crea** .

9. Nella pagina **nuova pagina Web part** assegnare un nome alla pagina **SampleWebPartPage. aspx**, quindi scegliere il pulsante **Crea** .

     Verrà visualizzata la pagina Web part.

10. Selezionare qualsiasi area nella pagina Web part.

11. Nella parte superiore della pagina scegliere la scheda **Inserisci** , quindi fare clic sul pulsante **Web part** .

12. Nel riquadro **categorie** scegliere la cartella **personalizzata** , scegliere la Web part **WebPart1** , quindi scegliere il pulsante **Aggiungi** .

     La Web part viene visualizzata nella pagina.

## <a name="test-the-custom-property"></a>Testare la proprietà personalizzata

Per popolare la griglia di dati visualizzata nella web part, specificare il percorso del file XML contenente i dati relativi a ogni dipendente.

1. Scegliere la freccia visualizzata sul lato destro della web part, quindi scegliere **Modifica web part** dal menu visualizzato.

     Sul lato destro della pagina viene visualizzato un riquadro contenente le proprietà della web part.

2. Nel riquadro espandere il nodo **varie** , immettere il percorso del file XML creato in precedenza, scegliere il pulsante **applica** , quindi scegliere il pulsante **OK** .

     Verificare che nella web part venga visualizzato un elenco di dipendenti.

## <a name="test-the-web-part-verb"></a>Testare il verbo della web part

Consente di visualizzare e nascondere i dipendenti che non sono responsabili selezionando un elemento visualizzato nel menu dei verbi della web part.

1. Scegliere la freccia visualizzata sul lato destro della web part, quindi scegliere **Mostra Manager solo** dal menu visualizzato.

     Solo i dipendenti responsabili sono visualizzati nella web part.

2. Scegliere di nuovo la freccia, quindi scegliere **Mostra tutti i dipendenti** dal menu visualizzato.

     Tutti i dipendenti vengono visualizzati nella web part.

## <a name="see-also"></a>Vedi anche

[Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Procedura: creare una Web part](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 di SharePoint [Procedura: creare una Web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 [Procedura dettagliata: creare una Web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
