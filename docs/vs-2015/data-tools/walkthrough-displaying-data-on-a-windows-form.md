---
title: 'Procedura dettagliata: Visualizzazione dei dati in un Windows Form | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- Windows applications, displaying data
- data binding, Windows Forms
- data [Visual Studio], displaying on Windows Forms
- forms, displaying data
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3decf0da6dd6d16c0128fdaeedf2fcd0cea94871
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530488"
---
# <a name="walkthrough-displaying-data-on-a-windows-form"></a>Procedura dettagliata: visualizzazione di dati in un Windows Form
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uno degli scenari più comuni nello sviluppo delle applicazioni è la visualizzazione dei dati di un form in un'applicazione per Windows. È possibile visualizzare i dati in un modulo trascinando elementi dal [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) nel form. Questa procedura dettagliata consente di creare un form semplice in cui vengono visualizzati i dati di una tabella in più controlli. In questo esempio viene usata la tabella `Customers` del database di esempio Northwind.  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di una nuova **applicazioni Windows** progetto.  
  
-   Creazione e configurazione di un set di dati con il [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Selezione del controllo da creare nel form quando si trascinano elementi dal **Zdroje dat** finestra. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creazione di un controllo con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind. Per altre informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-windows-application"></a>Creazione dell'applicazione Windows  
 Il primo passaggio consiste nel creare un **applicazioni Windows** progetto.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Per creare il nuovo progetto Applicazione Windows  
  
1.  Dal **File** menu, creare un nuovo progetto.  
  
2.  Denominare il progetto `DisplayingDataonaWindowsForm`.  
  
3.  Selezionare **applicazione di Windows** e fare clic su **OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il **DisplayingDataonaWindowsForm** viene creato e aggiunto al progetto **Esplora soluzioni**.  
  
## <a name="creating-the-data-source"></a>Creazione dell'origine dati  
 Questo passaggio viene creata un'origine dati usando il **configurazione guidata origine dati** base il `Customers` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione di database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nel **scegliere la connessione dati** eseguire pagina una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         oppure  
  
    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo...  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi fare clic su **successivo**.  
  
6.  Fare clic su **successivo** nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.  
  
7.  Espandere la **tabelle** nodo il **Scegli oggetti di Database** pagina.  
  
8.  Selezionare il **clienti** tabella e quindi fare clic su **fine**.  
  
     Il **NorthwindDataSet** viene aggiunto al progetto e il **clienti** inclusa nella tabella il **Zdroje dat** finestra.  
  
## <a name="setting-the-controls-to-be-created"></a>Impostazione dei controlli da creare  
 In questa procedura dettagliata i dati saranno presentati in una **dettagli** layout in cui i dati vengono visualizzati in singoli controlli. (L'approccio alternativo è il valore predefinito **griglia** layout in cui i dati vengono visualizzati in un <xref:System.Windows.Forms.DataGridView> controllo.)  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Per impostare il tipo di rilascio degli elementi della finestra Origini dati  
  
1.  Espandere la **clienti** nodo il **Zdroje dat** finestra.  
  
2.  Modificare il tipo di rilascio del **clienti** alla tabella **dettagli** selezionando **dettagli** nell'elenco a discesa nel **clienti** nodo. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Modifica il **CustomerID** tipo di rilascio della colonna a un'etichetta selezionando **Label** dall'elenco di controllo nel **CustomerID** nodo.  
  
## <a name="creating-the-form"></a>Creazione del form  
 Creare i controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form  
  
-   Trascinare l'oggetto principale **clienti** nodo dalle **Zdroje dat** finestra nei form.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Premere F5.  
  
-   Usare il controllo <xref:System.Windows.Forms.BindingNavigator> per spostarsi all'interno dei record.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un Windows Form associato a dati. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Aggiunta di funzionalità di ricerca al form. Per altre informazioni, vedere [procedura: aggiungere una Query con parametri a un'applicazione di Windows Forms](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Aggiungere funzionalità per l'invio di aggiornamenti al database. Per altre informazioni, vedere [procedura dettagliata: salvataggio di dati a un Database (a tabella singola)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
-   Aggiunta il `Orders` tabella al set di dati, selezionando **configura il DataSet con Creazione guidata** dall'interno la **Zdroje dat** finestra. Sarà quindi possibile aggiungere controlli che visualizzano dati correlati trascinando il **ordini** nodo (posto sotto il **Fax** colonna all'interno di **i clienti** tabella) nel form. Per altre informazioni, vedere [Procedura: Visualizzare dati correlati in un'applicazione Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)   
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)