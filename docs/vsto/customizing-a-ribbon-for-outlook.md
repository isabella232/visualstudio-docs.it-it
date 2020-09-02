---
title: Personalizzare una barra multifunzione per Outlook
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2865bd89da3b59a24208e07739e8c56254959c88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986100"
---
# <a name="customize-a-ribbon-for-outlook"></a>Personalizzare una barra multifunzione per Outlook
  Quando si personalizza la barra multifunzione in Microsoft Office Outlook, è necessario considerare la posizione in cui la barra multifunzione personalizzata verrà visualizzata nell'applicazione. Outlook visualizza la barra multifunzione nell'interfaccia utente principale dell'applicazione e nelle finestre aperte quando gli utenti eseguono determinate attività, ad esempio la creazione di messaggi di posta elettronica. Queste finestre dell'applicazione sono denominate controlli.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Aggiungere una barra multifunzione personalizzata all'interfaccia utente dell'applicazione principale
 L'interfaccia utente principale in Outlook è denominata Explorer. Se si usa l'elemento **barra multifunzione (finestra di progettazione visiva)** , è possibile aggiungere una barra multifunzione a Esplora risorse facendo clic sulla proprietà **RibbonType** della barra multifunzione nella finestra **proprietà** e quindi selezionando **Microsoft. Outlook. Explorer**.

## <a name="assign-a-ribbon-to-an-inspector"></a>Assegnare una barra multifunzione a un controllo
 Per identificare il controllo che si vuole personalizzare, specificare il tipo di barra multifunzione corrispondente alla classe messaggio per il controllo.

 Se si usa l'elemento **barra multifunzione (finestra di progettazione visiva)** , fare clic sulla proprietà **RibbonType** della barra multifunzione nella finestra **proprietà** , quindi selezionare uno o più ID della barra multifunzione nell'elenco di valori.

 È possibile aggiungere più barre multifunzione a un progetto. Se più barre multifunzione condividono uno stesso ID, eseguire l'override del metodo `CreateRibbonExtensibilityObject` nella classe `ThisAddin` del progetto per specificare la barra multifunzione da visualizzare in fase di esecuzione. Per altre informazioni, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md). Per ulteriori informazioni su ogni tipo di barra multifunzione, vedere l'articolo tecnico [personalizzare la barra multifunzione in Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Specificare il tipo di barra multifunzione tramite XML della barra multifunzione
 Se si usa l'elemento **barra multifunzione (XML)** , controllare il valore del parametro *ribbonID* nel <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodo e restituire la barra multifunzione appropriata.

 Il metodo <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> viene generato automaticamente da Visual Studio nel file di codice della barra multifunzione. Il parametro *ribbonID* è una stringa che identifica l'esploratore o un tipo specifico di Inspector. Per un elenco completo dei valori possibili del parametro *ribbonID* , vedere l'articolo tecnico [personalizzare la barra multifunzione in Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

 L'esempio di codice seguente illustra come visualizzare una barra multifunzione personalizzata solo nel controllo `Microsoft.Outlook.Mail.Compose`. Questo controllo viene visualizzato quando un utente crea un nuovo messaggio di posta elettronica. La barra multifunzione da visualizzare viene specificata nel `GetResourceText()` metodo, generato nella classe **Ribbon** . Per ulteriori informazioni sulla classe **Ribbon** , vedere [Ribbon XML](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>Vedere anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
