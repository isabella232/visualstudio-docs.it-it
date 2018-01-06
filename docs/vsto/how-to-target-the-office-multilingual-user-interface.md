---
title: 'Procedura: l''interfaccia utente multilingue di Office di destinazione | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3de0e73a4a5a5cf10cd0f378a2d00d3c4da1b2d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Procedura: utilizzare l'interfaccia utente multilingue (MUI) di Office
  Multilingual User Interface (MUI) è una funzionalità di Microsoft Office che consente all'utente finale la possibilità di modificare la lingua dell'interfaccia utente (UI). Ad esempio, un utente finale, utilizzo di un'interfaccia utente in inglese è possibile modificare la lingua dell'interfaccia utente per lo spagnolo.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se l'applicazione verrà utilizzata da persone che utilizzano più lingue di Office, è possibile aggiungere codice per modificare automaticamente la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua utilizzata dalle applicazioni di Office nel computer dell'utente (se l'utente ha installate le risorse corrette).  
  
### <a name="to-check-the-current-office-ui-setting"></a>Per controllare l'impostazione corrente dell'interfaccia utente di Office  
  
1.  Utilizzare il <xref:System.Threading.Thread.CurrentUICulture%2A> proprietà del thread corrente. Impostare la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua utilizzata dalla versione di Office attualmente in esecuzione nel computer dell'utente.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Vedere anche  
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)  
  
  