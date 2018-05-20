---
title: Azioni personalizzate nelle aree del modulo di Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec4c6a0ce361102ab216bc0c9f460a0bdd7a4a0d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="custom-actions-in-outlook-form-regions"></a>Azioni personalizzate nelle aree del modulo di Outlook
  Azioni visualizzano i pulsanti che consentono agli utenti di rispondere a un elemento di Microsoft Office Outlook. Per rispondere a un elemento di posta elettronica, ad esempio, gli utenti fanno clic il **risposta**, **Rispondi a tutti**, o **Avanti** pulsanti di azione. Ognuna di queste azioni crea un nuovo elemento di posta elettronica e popola i campi dell'elemento utilizzando le informazioni dell'elemento originale.  
  
 È possibile creare un'azione personalizzata che apre qualsiasi tipo di elemento di Outlook. Ad esempio, è possibile aggiungere un'azione personalizzata che consente di aprire un nuovo elemento di attività o l'appuntamento. Impostare le proprietà di un'azione personalizzata o utilizzare codice personalizzato per popolare i campi del nuovo elemento. Azioni personalizzate vengono visualizzate nel **azioni personalizzate** elenco a discesa di un elemento che è aperto in una finestra di controllo di Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-custom-actions-to-a-form-region"></a>Aggiungere azioni personalizzate a un'area del modulo  
 Per aggiungere un'azione personalizzata a un'area del modulo, utilizzare il **azioni personalizzate** la finestra di dialogo. È possibile aprire il **azioni personalizzate** nella finestra di dialogo **Esplora** espandendo il **manifesto** nodo, selezionando il **CustomActions**proprietà e quindi fare clic sul pulsante con puntini di sospensione (![ellisse della finestra di progettazione per dispositivi mobili ASP.NET](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")).  
  
 È possibile utilizzare il **azioni personalizzate** la finestra di dialogo per specificare un *form destinazione*. Un modulo di destinazione è il modulo che viene visualizzata quando l'utente esegue l'azione personalizzata.  
  
 È inoltre possibile utilizzare il **azioni personalizzate** finestra di dialogo per specificare la modalità di informazioni da visualizzare nel modulo di destinazione l'oggetto originale.  
  
 Nella tabella seguente vengono descritte le proprietà disponibili nel **azioni personalizzate** la finestra di dialogo.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**AddressLike**|Specifica come verrà risolti modulo di destinazione.|  
|**Corpo**|Specifica il modo in cui viene aggiunto il corpo dell'elemento originale nel modulo di destinazione.|  
|**Enabled**|Indica se l'azione personalizzata è abilitata. Se questa proprietà è impostata su **false**, l'azione personalizzata è disabilitata.|  
|**Metodo**|Specifica il tipo di risposta disponibile quando viene eseguita l'azione personalizzata. L'azione personalizzata può inviare il modulo, aprire il form o richiedere all'utente se si desidera inviare o aprire il form.|  
|**Name**|Specifica il nome interno che è possibile utilizzare per fare riferimento a questa azione personalizzata nel codice.|  
|**ShowOnRibbon**|Indica se visualizzare l'azione personalizzata sulla barra multifunzione dell'elemento originale.|  
|**SubjectPrefix**|Specifica il testo che viene inserito all'inizio della riga dell'oggetto del modulo di destinazione.|  
|**TargetForm**|Specifica il nome della classe messaggio del modulo di destinazione. Ad esempio, digitare **IPM. Attività** per aprire un modulo di attività.|  
|**Titolo**|Specifica l'etichetta del pulsante di azione personalizzata.|  
  
## <a name="customize-a-custom-action-at-runtime"></a>Personalizzare un'azione personalizzata in fase di esecuzione  
 È anche possibile aggiungere il comportamento all'azione personalizzata tramite codice. Ad esempio, è possibile aggiungere codice che accetta i nomi dei destinatari di posta elettronica e li aggiunge come partecipanti in un nuovo elemento appuntamento. A tale scopo, gestire il [CustomAction](http://msdn.microsoft.com/library/office/ff862186.aspx) evento del [oggetto MailItem](http://msdn.microsoft.com/library/office/ff861332.aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procedura dettagliata: Progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Associare un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  