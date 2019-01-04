---
title: 'Procedura dettagliata: Creazione di una Web Part per SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f2c851659d09cc118f8f54b6e82bb3b806d7e34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944285"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>Procedura dettagliata: Creare una web part per SharePoint

Le Web part consentono agli utenti di modificare direttamente il contenuto, l'aspetto e comportamento delle pagine del sito di SharePoint utilizzando un browser. Questa procedura dettagliata illustra come creare una Web Part tramite il **Web Part** modello di elemento in Visual Studio 2010.

La Web Part consente di visualizzare i dipendenti in una griglia dati. L'utente specifica il percorso del file che contiene i dati del dipendente. L'utente può anche filtrare la griglia dei dati in modo che vengano visualizzati i dipendenti che sono responsabili solo nell'elenco.

Questa procedura dettagliata illustra le attività seguenti:

- Creazione di una Web Part con Visual Studio **Web Part** modello di elemento.

- Creazione di una proprietà che può essere impostata dall'utente della Web Part. Questa proprietà specifica il percorso del file di dati dipendenti.

- Consente di controllare il rendering del contenuto in una Web Part aggiungendo i controlli Web Part di raccolta.

- Creazione di una nuova voce di menu, definito come un *verbo,* che viene visualizzato nel menu dei verbi della Web part sottoposto a rendering. I verbi consentono all'utente di modificare i dati visualizzati nella Web Part.

- Test della Web Part in SharePoint.

    > [!NOTE]
    > I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio 2017 o servizi di Azure DevOps.

## <a name="create-an-empty-sharepoint-project"></a>Creare un progetto SharePoint vuoto

In primo luogo, creare un progetto SharePoint vuoto. In seguito si aggiungerà una Web Part al progetto usando il **Web Part** modello di elemento.

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando il **Esegui come amministratore** opzione.

2. Nella barra dei menu, scegliere **File** > **New** > **progetto**.

3. Nel **nuovo progetto** finestra di dialogo espandere il **SharePoint** nodo sotto il linguaggio che si desidera usare e quindi scegliere il **2010** nodo.

4. Nel **modelli** riquadro, scegliere **progetto SharePoint 2010**e quindi scegliere il **OK** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzata. Questa procedura guidata consente di selezionare il sito che si utilizzerà per eseguire il debug del progetto e il livello di attendibilità della soluzione.

5. Scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante per accettare il sito di SharePoint locale predefinito.

## <a name="add-a-web-part-to-the-project"></a>Aggiungere una web part al progetto

Aggiungere un **Web Part** elemento al progetto. Il **Web Part** elemento aggiunge il file di codice di Web Part. In un secondo momento, si aggiungerà codice al file di codice di Web Part del rendering del contenuto della Web Part.

1. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

2. Nel **Aggiungi nuovo elemento** nella finestra di dialogo il **modelli installati** riquadro espandere la **SharePoint** nodo e quindi scegliere il **2010** nodo.

3. Nell'elenco dei modelli di SharePoint, scegliere il **Web Part** modello, quindi scegliere il **Add** pulsante.

     Il **Web Part** voce viene visualizzata nel **Esplora soluzioni**.

## <a name="rendering-content-in-the-web-part"></a>Il rendering del contenuto in una web part

È possibile specificare quali controlli da visualizzare nella Web Part aggiungendoli alla raccolta di controlli della classe Web Part.

1. Nelle **Esplora soluzioni**aprire *WebPart1.vb* (in Visual Basic) o *WebPart1.cs* (in c#).

     Il file di codice di Web Part viene aperto nell'Editor di codice.

2. Aggiungere le istruzioni seguenti all'inizio del file di codice della Web Part.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Aggiungere il codice seguente alla classe `WebPart1` . Questo codice dichiara i campi seguenti:

   - Una griglia di dati per visualizzare i dipendenti nella Web Part.

   - Testo visualizzato nel controllo a cui viene utilizzato per filtrare la griglia dei dati.

   - Un'etichetta che viene visualizzato un errore se la griglia dei dati è in grado di visualizzare i dati.

   - Stringa che contiene il percorso del file di dati dipendenti.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Aggiungere il codice seguente alla classe `WebPart1` . Questo codice aggiunge una proprietà personalizzata denominata `DataFilePath` alla Web Part. Una proprietà personalizzata è una proprietà che è possibile impostare in SharePoint dall'utente. Questa proprietà ottiene e imposta la posizione di un file di dati XML che viene usata per popolare la griglia dei dati.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Sostituire il metodo `CreateChildControls` con il codice seguente. Mediante il codice vengono effettuate le seguenti attività:

   - Aggiunge la griglia dei dati e l'etichetta che è stato dichiarato nel passaggio precedente.

   - Associa la griglia dei dati in un file XML che contiene i dati dei dipendenti.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Aggiungere il metodo seguente alla classe `WebPart1` . Mediante il codice vengono effettuate le seguenti attività:

   - Crea un verbo visualizzata nel menu dei verbi Web Part della Web part sottoposto a rendering.

   - Gestione dell'evento generato quando l'utente sceglie il verbo nel relativo menu. Questo codice filtra l'elenco di dipendenti che viene visualizzato nella griglia dei dati.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Testare la web part

Quando si esegue il progetto, viene aperto il sito di SharePoint. La Web Part viene automaticamente aggiunto alla raccolta Web Part in SharePoint. È possibile aggiungere la Web Part a qualsiasi pagina Web Part.

1. Incollare il codice XML seguente in un file di blocco note. Questo file XML contiene i dati di esempio che verranno visualizzato nella Web Part.

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

2. Nel blocco note, sulla barra dei menu, scegliere **File** > **Salva con nome**.

3. Nel **Salva con nome** nella finestra di dialogo il **Salva come tipo** scegliere **tutti i file**.

4. Nel **nomefile** casella, immettere **Data. XML**.

5. Scegliere una cartella utilizzando la **Sfoglia cartelle** pulsante e quindi scegliere il **salvare** pulsante.

6. In Visual Studio, scegliere il **F5** chiave.

     Viene aperto il sito di SharePoint.

7. Nel **Azioni sito** menu, scegliere **altre opzioni**.

8. Nel **Create** pagina, scegliere il **Web Part Page** digitare e quindi scegliere il **Create** pulsante.

9. Nel **nuova pagina Web Part** pagina, denominare la pagina **SampleWebPartPage. aspx**, quindi scegliere il **crea** pulsante.

     Viene visualizzata la pagina Web Part.

10. Selezionare qualsiasi area della pagina Web Part.

11. Nella parte superiore della pagina, scegliere il **inserire** scheda e quindi scegliere il **Web Part** pulsante.

12. Nel **categorie** riquadro, scegliere il **Custom** cartella, scegliere il **WebPart1** Web Part e quindi scegliere il **Aggiungi** pulsante.

     La Web Part viene visualizzata nella pagina.

## <a name="test-the-custom-property"></a>Testare la proprietà personalizzata

Per popolare la griglia dati che viene visualizzato nella Web Part, specificare il percorso del file XML che contiene dati relativi a ogni dipendente.

1. Scegliere la freccia visualizzata a destra della Web Part e quindi scegliere **modifica Web Part** dal menu visualizzato.

     Sul lato destro della pagina viene visualizzato un riquadro che contiene le proprietà per la Web Part.

2. Nel riquadro, espandere la **varie** nodo, immettere il percorso del file XML creato in precedenza, scegliere il **Apply** pulsante e quindi scegliere il **OK** pulsante.

     Verificare che venga visualizzato un elenco di dipendenti nella Web Part.

## <a name="test-the-web-part-verb"></a>Verbo della web part di test

Mostrare e nascondere i dipendenti che non sono Manager facendo clic su un elemento visualizzato nel menu dei verbi Web Part.

1. Scegliere la freccia visualizzata a destra della Web Part e quindi scegliere **Mostra solo i responsabili** dal menu visualizzato.

     Solo i dipendenti che sono Manager vengono visualizzati nella Web Part.

2. Scegliere nuovamente la freccia e quindi scegliere **visualizzare tutti i dipendenti** dal menu visualizzato.

     Tutti i dipendenti vengono visualizzati nella Web Part.

## <a name="see-also"></a>Vedere anche

[Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Procedura: Creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Procedura: Creare una web part di SharePoint usando una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[Procedura dettagliata: Creare una web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
