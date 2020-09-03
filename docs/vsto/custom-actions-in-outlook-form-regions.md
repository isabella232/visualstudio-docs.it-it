---
title: Azioni personalizzate nelle aree del modulo di Outlook
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 817cf9fe8698c2908e873246a8971f90fe72b460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254446"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Azioni personalizzate nelle aree del modulo di Outlook
  Azioni visualizzano i pulsanti che consentono agli utenti di rispondere a un Microsoft Office elemento Outlook. Ad esempio, per rispondere a un elemento di posta elettronica, gli utenti fanno clic sui pulsanti **Rispondi**, **Rispondi a tutti**o Esegui azione di **inoltro** . Ognuna di queste azioni crea un nuovo elemento di posta elettronica e popola i campi dell'elemento usando le informazioni dell'elemento originale.

 È possibile creare un'azione personalizzata che apre qualsiasi tipo di elemento di Outlook. Ad esempio, è possibile aggiungere un'azione personalizzata che apre un nuovo appuntamento o un nuovo elemento di attività. Impostare le proprietà di un'azione personalizzata o usare codice personalizzato per popolare i campi del nuovo elemento. Le azioni personalizzate vengono visualizzate nell'elenco a discesa **azioni personalizzate** di un elemento aperto in una finestra di controllo di Outlook.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Aggiungere azioni personalizzate a un'area del modulo
 Per aggiungere un'azione personalizzata a un'area del modulo, utilizzare la finestra di dialogo **azioni personalizzate** . È possibile aprire la finestra di dialogo **azioni personalizzate** selezionando l'area del modulo in **Esplora soluzioni**, espandendo il nodo **manifesto** nella **finestra Proprietà**, selezionando la proprietà **CustomActions** , quindi facendo clic sul pulsante con i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")).

 È possibile utilizzare la finestra di dialogo **azioni personalizzate** per specificare un *modulo di destinazione*. Un modulo di destinazione è il modulo che viene visualizzato quando l'utente esegue l'azione personalizzata.

 È inoltre possibile utilizzare la finestra di dialogo **azioni personalizzate** per specificare come si desidera che le informazioni dell'elemento originale vengano visualizzate nel modulo di destinazione.

 Nella tabella seguente vengono descritte le proprietà disponibili nella finestra di dialogo **azioni personalizzate** .

|Proprietà|Descrizione|
|--------------|-----------------|
|**AddressLike**|Consente di specificare la modalità di indirizzamento del modulo di destinazione.|
|**Corpo**|Specifica il modo in cui il corpo dell'elemento originale viene aggiunto al form di destinazione.|
|**Attivata**|Indica se l'azione personalizzata è abilitata. Se questa proprietà è impostata su **false**, l'azione personalizzata è disabilitata.|
|**Metodo**|Specifica il tipo di risposta disponibile quando viene eseguita l'azione personalizzata. L'azione personalizzata può inviare il modulo, aprire il modulo o richiedere all'utente se vuole inviare o aprire il modulo.|
|**Name**|Specifica il nome interno che è possibile usare per fare riferimento a questa azione personalizzata nel codice.|
|**ShowOnRibbon**|Indica se visualizzare l'azione personalizzata sulla barra multifunzione dell'elemento originale.|
|**SubjectPrefix**|Specifica il testo che viene inserito all'inizio della riga dell'oggetto del form di destinazione.|
|**TargetForm**|Specifica il nome della classe del messaggio del form di destinazione. Inserire, ad esempio, **IPM. Attività** per l'apertura di un form attività.|
|**Title**|Specifica l'etichetta del pulsante di azione personalizzato.|

## <a name="customize-a-custom-action-at-run-time"></a>Personalizzare un'azione personalizzata in fase di esecuzione
 È anche possibile aggiungere il comportamento all'azione personalizzata usando il codice. Ad esempio, è possibile aggiungere il codice che accetta i nomi dei destinatari di posta elettronica e aggiunge tali nomi come partecipanti in un nuovo elemento appuntamento. A tale scopo, gestire l'evento [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) dell' [oggetto MailItem](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Vedere anche
- [Creazione di aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Associare un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
