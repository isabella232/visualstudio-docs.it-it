---
title: "Procedura: utilizzare l'interfaccia utente multilingue di Office"
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5217f2d6cf67eced00c0c84b9bacda94573c5a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537501"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Procedura: utilizzare l'interfaccia utente multilingue di Office
  L'interfaccia utente multilingue (MUI) è una funzionalità Microsoft Office che consente all'utente finale di modificare la lingua dell'interfaccia utente (UI). Ad esempio, un utente finale che lavora con un'interfaccia utente inglese può modificare la lingua dell'interfaccia utente in spagnolo.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Se l'applicazione verrà utilizzata dagli utenti che utilizzano molte lingue di Office, è possibile aggiungere codice per modificare automaticamente la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua utilizzata da Office nel computer dell'utente (se l'utente dispone delle risorse corrette installate).

## <a name="to-check-the-current-office-ui-setting"></a>Per verificare l'impostazione corrente dell'interfaccia utente di Office

1. Utilizzare la <xref:System.Threading.Thread.CurrentUICulture%2A> proprietà del thread corrente. Impostare la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua utilizzata dalla versione di Office attualmente in esecuzione nel computer dell'utente.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Vedere anche
- [Procedura: destinare applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)
