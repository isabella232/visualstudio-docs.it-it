---
title: Personalizzare una barra multifunzione per Outlook
description: Quando si personalizza la barra multifunzione in Microsoft Office Outlook, è necessario considerare la posizione in cui verrà visualizzata la barra multifunzione personalizzata nell'applicazione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3c3b200a63ed17afbf4068475ae1509f1bf0da80
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710102"
---
# <a name="customize-a-ribbon-for-outlook"></a>Personalizzare una barra multifunzione per Outlook
  Quando si personalizza la barra multifunzione in Microsoft Office Outlook, è necessario considerare la posizione in cui la barra multifunzione personalizzata verrà visualizzata nell'applicazione. Outlook visualizza la barra multifunzione nell'interfaccia utente principale dell'applicazione e nelle finestre aperte quando gli utenti eseguono determinate attività, ad esempio la creazione di messaggi di posta elettronica. Queste finestre dell'applicazione sono denominate controlli.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Aggiungere una barra multifunzione personalizzata all'interfaccia utente principale dell'applicazione
 L'interfaccia utente principale in Outlook è denominata Explorer. Se si usa l'elemento Barra multifunzione (finestra di progettazione **visiva),** è possibile aggiungere una  barra multifunzione a Esplora risorse facendo clic sulla proprietà **RibbonType** della barra multifunzione nella finestra Proprietà e quindi selezionando **Microsoft.Outlook. Esplora risorse**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Assegnare una barra multifunzione a un controllo
 Per identificare il controllo che si vuole personalizzare, specificare il tipo di barra multifunzione corrispondente alla classe messaggio per il controllo.

 Se si usa l'elemento Barra multifunzione **(finestra** di progettazione visiva), fare clic sulla proprietà **RibbonType** della barra multifunzione nella finestra Proprietà e quindi selezionare uno o più ID della barra multifunzione dall'elenco di valori. 

 È possibile aggiungere più barre multifunzione a un progetto. Se più barre multifunzione condividono uno stesso ID, eseguire l'override del metodo `CreateRibbonExtensibilityObject` nella classe `ThisAddin` del progetto per specificare la barra multifunzione da visualizzare in fase di esecuzione. Per altre informazioni, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md) Per altre informazioni su ogni tipo di barra multifunzione, vedere l'articolo tecnico Personalizzare la barra [multifunzione in Outlook 2007.](/previous-versions/office/developer/office-2007/bb226712(v=office.12))

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Specificare il tipo di barra multifunzione usando l'XML della barra multifunzione
 Se si usa **l'elemento Barra multifunzione (XML),** controllare il valore del parametro *ribbonID* nel metodo e <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> restituire la barra multifunzione appropriata.

 Il metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> viene generato automaticamente da Visual Studio nel file di codice della barra multifunzione. Il *parametro ribbonID* è una stringa che identifica explorer o un tipo specifico di controllo. Per un elenco completo dei valori possibili del parametro *ribbonID,* vedere l'articolo tecnico Personalizzare la barra [multifunzione in Outlook 2007.](/previous-versions/office/developer/office-2007/bb226712(v=office.12))

 L'esempio di codice seguente illustra come visualizzare una barra multifunzione personalizzata solo nel controllo `Microsoft.Outlook.Mail.Compose`. Questo controllo viene visualizzato quando un utente crea un nuovo messaggio di posta elettronica. La barra multifunzione da visualizzare viene specificata nel `GetResourceText()` metodo , generato nella classe **Ribbon.** Per altre informazioni sulla classe **Ribbon,** vedere [Xml della barra multifunzione.](../vsto/ribbon-xml.md)

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb" id="Snippet1":::

## <a name="see-also"></a>Vedi anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
