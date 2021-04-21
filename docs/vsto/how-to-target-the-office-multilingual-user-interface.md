---
title: "Procedura: Impostare come destinazione l'interfaccia utente multilingue di Office"
description: Informazioni su come usare i Visual Studio a livello di codice per Microsoft Office'interfaccia utente multilingue.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3cf838b544ec78c8c7d6e9e2d6f1cb747e999ccd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823914"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Procedura: Impostare come destinazione l'interfaccia utente multilingue di Office
  Il interfaccia utente multilingue (MUI) è una funzionalità Microsoft Office che offre all'utente finale la possibilità di modificare la lingua dell'interfaccia utente. Ad esempio, un utente finale che lavora con un'interfaccia utente in inglese può modificare la lingua dell'interfaccia utente in spagnolo.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Se l'applicazione verrà usata da utenti che usano molte lingue di Office, è possibile aggiungere codice per modificare automaticamente la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua usata da Office nel computer dell'utente (se l'utente ha installato le risorse corrette).

## <a name="to-check-the-current-office-ui-setting"></a>Per controllare l'impostazione corrente dell'interfaccia utente di Office

1. Usare la <xref:System.Threading.Thread.CurrentUICulture%2A> proprietà del thread corrente. Impostare la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua usata dalla versione di Office attualmente in esecuzione nel computer dell'utente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Impostare come destinazione le applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)
