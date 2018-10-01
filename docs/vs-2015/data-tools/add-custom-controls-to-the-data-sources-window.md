---
title: Aggiungere controlli personalizzati alla finestra Origini dati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: acdab62754a8cbbe7b97ea9723fba202d5078ac0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529073"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Aggiungere controlli personalizzati alla finestra Origini dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiungere controlli personalizzati alla finestra Origini dei dati](https://docs.microsoft.com/visualstudio/data-tools/add-custom-controls-to-the-data-sources-window).  
  
  
Quando si trascina un elemento dal **Zdroje dat** finestra per un'area di progettazione per creare un controllo con associazione a dati, è possibile selezionare il tipo di controllo da creare. Ogni elemento nella finestra ha un elenco di riepilogo a discesa che visualizza i controlli che è possibile scegliere tra. Il set di controlli associati a ogni elemento è determinato dal tipo di dati dell'elemento. Se il controllo che si desidera creare non viene visualizzato nell'elenco, è possibile seguire le istruzioni in questo argomento per aggiungere il controllo all'elenco.  
  
 Per altre informazioni sulla selezione di controlli con associazione a dati da creare per gli elementi di **Zdroje dat** finestra, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, scegliere il **degli strumenti** dal menu **Importa / Esporta impostazioni**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="customizinglist"></a> Personalizzare l'elenco dei controlli associabili per un tipo di dati  
 Per aggiungere o rimuovere i controlli dall'elenco dei controlli disponibili per gli elementi di **Zdroje dat** finestra con un tipo di dati specifico, eseguire la procedura seguente.  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Per selezionare i controlli a essere elencati per un tipo di dati  
  
1.  Assicurarsi che sia aperta la finestra di progettazione Windows Form o WPF Designer.  
  
2.  Nel **Zdroje dat** finestra, fare clic su un elemento che fa parte di un'origine dati è stato aggiunto alla finestra e quindi scegliere il menu di scelta rapida per l'elemento.  
  
3.  Nel menu di riepilogo a discesa, fare clic su **Personalizza**. Si apre una delle finestre di dialogo seguenti:  
  
    -   Se la finestra di progettazione Windows Form è aperto, il **personalizzazione dell'interfaccia utente di dati** pagina della **opzioni** verrà visualizzata la finestra di dialogo.  
  
    -   Se la finestra di progettazione WPF è aperta, il **Personalizza associazione controlli** verrà visualizzata la finestra di dialogo.  
  
4.  Nella finestra di dialogo, selezionare un tipo di dati dal **tipo di dati** elenco a discesa.  
  
    -   Per personalizzare l'elenco di controlli per una tabella o oggetto, selezionare **[elenco]**.  
  
    -   Per personalizzare l'elenco di controlli per una colonna di una tabella o una proprietà di un oggetto, selezionare il tipo di dati della colonna o proprietà nell'archivio dati sottostante.  
  
    -   Per personalizzare l'elenco di controlli per visualizzare gli oggetti dati che includono forme definite dall'utente, selezionare **[altro]**. Ad esempio, selezionare **[altro]** se l'applicazione include un controllo personalizzato che consente di visualizzare i dati da più di una proprietà di un oggetto specifico.  
  
5.  Nel **associati a controlli** selezionare ogni controllo che si desidera rendere disponibili per il tipo di dati selezionato o annullare la selezione di tutti i controlli che si desidera rimuovere dall'elenco.  
  
    > [!NOTE]
    >  Se il controllo che si desidera selezionare non viene visualizzato nei **associati a controlli** casella, è necessario aggiungere il controllo all'elenco. Per altre informazioni, vedere [aggiunta di controlli per l'elenco di controlli associati a un tipo di dati](#addingcontrols).  
  
6.  Fare clic su **OK**.  
  
7.  Nel **Zdroje dat** finestra, fare clic su un elemento dei dati di tipo che sono stati appena associati uno o più controlli e quindi scegliere il menu di scelta rapida per l'elemento.  
  
     I controlli selezionati nel **associati a controlli** casella vengono ora visualizzati nel menu di riepilogo a discesa per l'elemento.  
  
##  <a name="addingcontrols"></a> Addcontrols all'elenco dei controlli associati a un tipo di dati  
 Se si desidera associare un controllo a un tipo di dati, ma il controllo non viene visualizzato nei **associati a controlli** casella, è necessario aggiungere il controllo all'elenco. Il controllo deve essere posizionato nella soluzione corrente o in un assembly di riferimento. Deve anche essere disponibile nel **casella degli strumenti**, e hanno un attributo che specifica il comportamento di associazione dati del controllo.  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Per aggiungere controlli all'elenco dei controlli associati  
  
1.  Aggiungere il controllo desiderato per il **casella degli strumenti** facendo clic con il **della casella degli strumenti** e scegliendo **Scegli elementi**.  
  
     Il controllo deve avere uno dei seguenti attributi.  
  
    |Attributo|Descrizione|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementare questo attributo su controlli semplici che consentono di visualizzare una singola colonna o proprietà, dei dati, ad esempio un <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementare questo attributo per i controlli che visualizzano elenchi (o tabelle) dei dati, ad esempio un <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementare questo attributo per i controlli che visualizzano elenchi (o tabelle) di dati, ma anche necessità di presentare una singola colonna o proprietà, ad esempio un <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Per i moduli di Windows, nel **opzioni** finestra di dialogo, aprire il **personalizzazione dell'interfaccia utente dati** pagina. In alternativa, per WPF, aprire il **Personalizza associazione controlli** nella finestra di dialogo. Per altre informazioni, vedere [personalizzazione dell'elenco di controlli associabili per un tipo di dati](#customizinglist).  
  
3.  Nel **associati a controlli** casella, il controllo appena aggiunto per il **della casella degli strumenti** dovrebbe ora essere visualizzato.  
  
    > [!NOTE]
    >  Solo i controlli che si trovano all'interno della soluzione corrente o in un assembly di riferimento possono essere aggiunti all'elenco dei controlli associati. (I controlli devono inoltre implementare uno degli attributi di associazione dati nella tabella precedente.) Per associare dati a un controllo personalizzato che non è disponibile nel **Zdroje dat** finestra, trascinare il controllo dal **della casella degli strumenti** nell'area di progettazione e quindi trascina l'elemento da associare dal **dati Origini** finestra al controllo.  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

