---
title: Personalizzare una barra multifunzione per Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef1c72d5c24c70a539b909e8d338a235ceb52a49
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="customize-a-ribbon-for-outlook"></a>Personalizzare una barra multifunzione per Outlook
  Quando si personalizza la barra multifunzione in Microsoft Office Outlook, è necessario considerare la posizione in cui la barra multifunzione personalizzata verrà visualizzata nell'applicazione. Outlook visualizza la barra multifunzione nell'interfaccia utente principale dell'applicazione e nelle finestre aperte quando gli utenti eseguono determinate attività, ad esempio la creazione di messaggi di posta elettronica. Queste finestre dell'applicazione sono denominate controlli.  
  
 ![collegamento alla trasmissione video](../vsto/media/playvideo.gif "collegamento alla trasmissione video") per una dimostrazione video correlata, vedere [procedura ricerca per categorie: utilizzare la finestra di progettazione della barra multifunzione per personalizzare la barra multifunzione in Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Aggiungere una barra multifunzione personalizzata all'applicazione principale dell'interfaccia utente  
 L'interfaccia utente principale in Outlook è denominata Explorer. Se si utilizza il **della barra multifunzione (finestra di progettazione visiva)** item, è possibile aggiungere una barra multifunzione a Esplora facendo il **RibbonType** proprietà della barra multifunzione nel **proprietà** finestra e quindi selezionando **Microsoft**.  
  
## <a name="assign-a-ribbon-to-an-inspector"></a>Assegnare una barra multifunzione a un controllo  
 Per identificare il controllo che si vuole personalizzare, specificare il tipo di barra multifunzione corrispondente alla classe messaggio per il controllo.  
  
 Se si utilizza il **della barra multifunzione (finestra di progettazione visiva)** fare clic sul **RibbonType** proprietà della barra multifunzione di **proprietà** gli ID di barra multifunzione finestra e quindi selezionare uno o più l'elenco di valori.  
  
 È possibile aggiungere più barre multifunzione a un progetto. Se più barre multifunzione condividono uno stesso ID, eseguire l'override del metodo `CreateRibbonExtensibilityObject` nella classe `ThisAddin` del progetto per specificare la barra multifunzione da visualizzare in fase di esecuzione. Per altre informazioni, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md). Per ulteriori informazioni su ogni tipo di barra multifunzione, vedere l'articolo tecnico [personalizzare la barra multifunzione in Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Specificare il tipo di barra multifunzione tramite XML barra multifunzione  
 Se si utilizza il **della barra multifunzione (XML)** voce, controllare il valore della *ribbonID* parametro il <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodo e restituire la barra multifunzione appropriata.  
  
 Il metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> viene generato automaticamente da Visual Studio nel file di codice della barra multifunzione. Il *ribbonID* parametro è una stringa che identifica l'interfaccia Explorer o un tipo specifico di controllo. Per un elenco completo dei valori possibili del *ribbonID* parametro, vedere l'articolo tecnico [personalizzare la barra multifunzione in Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 L'esempio di codice seguente illustra come visualizzare una barra multifunzione personalizzata solo nel controllo `Microsoft.Outlook.Mail.Compose`. Questo controllo viene visualizzato quando un utente crea un nuovo messaggio di posta elettronica. La barra multifunzione da visualizzare viene specificata nel `GetResourceText()` metodo, che viene generato nel **della barra multifunzione** classe. Per ulteriori informazioni sul **della barra multifunzione** classe, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [XML della barra multifunzione](../vsto/ribbon-xml.md)  
  
  