---
title: "Procedura: Impostare come destinazione l Office'interfaccia utente multilingue"
description: Informazioni su come usare i Visual Studio a livello di codice per l'Microsoft Office utente multilingue.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c6d3c98f2b9675681aacbd84d9abd8f919eb69ee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147934"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Procedura: Impostare come destinazione l Office'interfaccia utente multilingue
  Il interfaccia utente multilingue (MUI) è una funzionalità Microsoft Office che offre all'utente finale la possibilità di modificare la lingua dell'interfaccia utente. Ad esempio, un utente finale che lavora con un'interfaccia utente in inglese può modificare la lingua dell'interfaccia utente in spagnolo.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Se l'applicazione verrà usata da utenti che usano molte lingue di Office, è possibile aggiungere codice per modificare automaticamente la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua usata da Office nel computer dell'utente (se l'utente ha installato le risorse corrette).

## <a name="to-check-the-current-office-ui-setting"></a>Per controllare l'impostazione dell'interfaccia Office corrente

1. Usare la <xref:System.Threading.Thread.CurrentUICulture%2A> proprietà del thread corrente. Impostare la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua usata dalla versione di Office attualmente in esecuzione nel computer dell'utente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Impostare come destinazione Office applicazioni tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Associazione tardiva in Office soluzioni](../vsto/late-binding-in-office-solutions.md)
