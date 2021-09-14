---
title: Azioni personalizzate nelle aree Outlook modulo
description: Informazioni su come i pulsanti di visualizzazione delle azioni, ad esempio Rispondi e Rispondi a tutti, consentono agli utenti di rispondere a un Microsoft Office Outlook elemento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 75fcc83dc06a9503b5ab1571315dc95028734446
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710100"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Azioni personalizzate nelle aree Outlook modulo
  Le azioni visualizzano pulsanti che consentono agli utenti di rispondere a un Microsoft Office Outlook elemento. Ad esempio, per rispondere a un elemento di posta elettronica, gli utenti fare clic sui pulsanti **di** azione **Rispondi,** Rispondi a tutti **o** Inoltra. Ognuna di queste azioni crea un nuovo elemento di posta elettronica e popola i campi dell'elemento usando le informazioni dell'elemento originale.

 È possibile creare un'azione personalizzata che apre qualsiasi tipo di Outlook elemento. Ad esempio, è possibile aggiungere un'azione personalizzata che apre un nuovo appuntamento o un nuovo elemento attività. Impostare le proprietà di un'azione personalizzata o usare codice personalizzato per popolare i campi del nuovo elemento. Le azioni personalizzate vengono visualizzate **nell'elenco** a discesa Azioni personalizzate di un elemento aperto in una Outlook di controllo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Aggiungere azioni personalizzate a un'area del modulo
 Per aggiungere un'azione personalizzata a un'area del modulo, usare la **finestra di dialogo Azioni** personalizzate . È possibile  aprire la finestra di dialogo Azioni personalizzate selezionando l'area del modulo **in Esplora soluzioni**, espandendo il nodo Manifesto nella finestra Proprietà **,** selezionando la **proprietà CustomActions** e facendo clic sul pulsante con i puntini di sospensione ( ASP.NET puntini di sospensione della finestra di ![progettazione](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")per dispositivi mobili ). 

 È possibile utilizzare la **finestra di dialogo Azioni** personalizzate per specificare un modulo di *destinazione.* Un modulo di destinazione è il modulo che viene visualizzato quando l'utente esegue l'azione personalizzata.

 È anche possibile usare la **finestra di** dialogo Azioni personalizzate per specificare come si desidera che le informazioni dell'elemento originale vengano visualizzate nel modulo di destinazione.

 Nella tabella seguente vengono descritte le proprietà disponibili nella **finestra di dialogo Azioni** personalizzate .

|Proprietà|Descrizione|
|--------------|-----------------|
|**AddressLike**|Specifica come verrà indirizzato il modulo di destinazione.|
|**Corpo**|Specifica il modo in cui il corpo dell'elemento originale viene aggiunto al modulo di destinazione.|
|**Enabled**|Indica se l'azione personalizzata è abilitata. Se questa proprietà è impostata su **false**, l'azione personalizzata è disabilitata.|
|**Metodo**|Specifica il tipo di risposta disponibile quando viene eseguita l'azione personalizzata. L'azione personalizzata può inviare il modulo, aprire il modulo o richiedere all'utente se desidera inviare o aprire il modulo.|
|**Nome**|Specifica il nome interno che è possibile usare per fare riferimento a questa azione personalizzata nel codice.|
|**ShowOnRibbon**|Indica se visualizzare l'azione personalizzata sulla barra multifunzione dell'elemento originale.|
|**SubjectPrefix**|Specifica il testo inserito all'inizio della riga dell'oggetto del modulo di destinazione.|
|**TargetForm**|Specifica il nome della classe di messaggio del modulo di destinazione. Ad esempio, digitare **IPM. Attività** per aprire un modulo attività.|
|**Title**|Specifica l'etichetta del pulsante di azione personalizzata.|

## <a name="customize-a-custom-action-at-run-time"></a>Personalizzare un'azione personalizzata in fase di esecuzione
 È anche possibile aggiungere il comportamento all'azione personalizzata usando il codice. Ad esempio, è possibile aggiungere codice che accetta i nomi dei destinatari di posta elettronica e li aggiunge come partecipanti in un nuovo elemento appuntamento. A tale scopo, gestire [l'evento CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) [dell'oggetto MailItem](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Vedi anche
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: Progettare un'area Outlook modulo](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Associare un'area del modulo a una Outlook di messaggio](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
