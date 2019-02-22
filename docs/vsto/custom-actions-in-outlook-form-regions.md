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
ms.openlocfilehash: ea4cd33c67cfbd2d2150fceacaf0399810db0ca4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638036"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Azioni personalizzate nelle aree del modulo di Outlook
  Azioni di visualizzano i pulsanti che consentono agli utenti di rispondere a un elemento di Microsoft Office Outlook. Ad esempio, per rispondere a un elemento di posta elettronica, gli utenti fanno clic la **Reply**, **Rispondi a tutti**, o **inoltrare** pulsanti di azione. Ognuna di queste azioni crea un nuovo elemento di posta elettronica e popola i campi dell'elemento utilizzando le informazioni dell'elemento originale.

 È possibile creare un'azione personalizzata che si apre qualsiasi tipo di elemento di Outlook. Ad esempio, è possibile aggiungere un'azione personalizzata che si apre un nuovo elemento di attività o appuntamenti. Impostare le proprietà di un'azione personalizzata o usare codice personalizzato per popolare i campi del nuovo elemento. Azioni personalizzate vengono visualizzate nel **azioni personalizzate** elenco a discesa di un elemento che è aperto in una finestra di controllo di Outlook.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Aggiungere azioni personalizzate per un'area del modulo
 Per aggiungere un'azione personalizzata a un'area del modulo, usare il **azioni personalizzate** nella finestra di dialogo. È possibile aprire il **azioni personalizzate** nella finestra di dialogo **Esplora soluzioni** espandendo il **manifesto** nodo, selezionando il **elementi CustomAction**proprietà e quindi fare clic sul pulsante con puntini di sospensione (![ellisse della finestra di progettazione mobile ASP.NET](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")).

 È possibile usare la **azioni personalizzate** finestra di dialogo per specificare una *form destinazione*. Un modulo di destinazione è il modulo visualizzato quando l'utente esegue l'azione personalizzata.

 È anche possibile usare la **azioni personalizzate** finestra di dialogo per specificare come si desidera che le informazioni dell'elemento originale venga visualizzato nel modulo di destinazione.

 Nella tabella seguente vengono descritte le proprietà disponibili nel **azioni personalizzate** nella finestra di dialogo.

|Proprietà|Descrizione|
|--------------|-----------------|
|**AddressLike**|Specifica come il modulo di destinazione verrà risolti.|
|**Corpo**|Specifica come il corpo dell'elemento originale viene aggiunto al modulo di destinazione.|
|**Enabled**|Indica se è abilitata l'azione personalizzata. Se questa proprietà è impostata su **false**, l'azione personalizzata è disabilitato.|
|**Metodo**|Specifica il tipo di risposta disponibile quando viene eseguita l'azione personalizzata. L'azione personalizzata può inviare il modulo, aprire il form o richiedere all'utente se si desidera inviare o aprire il form.|
|**Name**|Specifica il nome interno che è possibile usare per fare riferimento a questa azione personalizzata nel codice.|
|**ShowOnRibbon**|Indica se visualizzare l'azione personalizzata sulla barra multifunzione dell'elemento originale.|
|**SubjectPrefix**|Specifica testo che viene inserito all'inizio della riga dell'oggetto di destinazione.|
|**TargetForm**|Specifica il nome della classe messaggio del modulo di destinazione. Ad esempio, digitare **IPM. Attività** per aprire un modulo di attività.|
|**Titolo**|Specifica l'etichetta del pulsante di azione personalizzata.|

## <a name="customize-a-custom-action-at-runtime"></a>Personalizzare un'azione personalizzata in fase di esecuzione
 È anche possibile aggiungere il comportamento per l'azione personalizzata usando il codice. Ad esempio, è possibile aggiungere codice che accetta i nomi dei destinatari di posta elettronica e aggiunge i nomi come partecipanti a un nuovo elemento appuntamento. A tale scopo, gestire le [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) eventi delle [oggetto MailItem](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Vedere anche
- [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)
- [Procedura dettagliata: Progettare un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Associare un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
