---
title: "Procedura: Destinazione dell'interfaccia utente multilingue di Office"
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 5180780835f36768cef77207189a1346c1dccdca
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866516"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Procedura: Destinazione dell'interfaccia utente multilingue di Office
  Multilingual User Interface (MUI) è una funzionalità di Microsoft Office che offre la possibilità di modificare la lingua dell'interfaccia utente (UI) l'utente finale. Ad esempio, un utente finale, uso di un'interfaccia utente in inglese possono modificare la lingua dell'interfaccia utente per spagnolo.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se l'applicazione verrà utilizzata da persone che utilizzano molte lingue di Office, è possibile aggiungere codice per modificare automaticamente la lingua delle stringhe dell'interfaccia utente in modo che corrisponda alla lingua utilizzata da Office nel computer dell'utente (se l'utente dispone di risorse corrette installate).  
  
## <a name="to-check-the-current-office-ui-setting"></a>Per controllare l'impostazione corrente dell'interfaccia utente di Office  
  
1.  Usare il <xref:System.Threading.Thread.CurrentUICulture%2A> proprietà del thread corrente. Impostare la lingua delle stringhe dell'interfaccia utente in base alla lingua usata dalla versione di Office che attualmente viene eseguito nel computer dell'utente.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Sviluppare applicazioni di Office tramite assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)  
