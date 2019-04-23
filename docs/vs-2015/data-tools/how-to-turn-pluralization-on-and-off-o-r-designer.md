---
title: 'Procedura: Attivare e disattivare (O-R Designer) la pluralizzazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6171ca233af1ec2af71f11d3248a9d2e670c156b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665857"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Procedura: Attivare e disattivare la pluralizzazione (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per impostazione predefinita, quando si trascinano oggetti di database con nomi che terminano in s o ies da **Esplora Server**/**Database Explorer** nel [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), i nomi delle classi di entità generate vengono modificati dal plurale al singolare. Questa modifica viene apportata per rappresentare in modo più preciso il fatto che viene eseguito il mapping della classe di entità, di cui è stata creata un'istanza, a un singolo record di dati. Ad esempio, l'aggiunta di una tabella Customers a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] determina una classe di entità denominata Customer poiché conterrà dati relativi a un solo cliente.  
  
> [!NOTE]
>  La pluralizzazione viene attivata per impostazione predefinita solo nella versione in lingua inglese di Visual Studio.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Per attivare e disattivare la pluralizzazione  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere **Strumenti di database**.  
  
> [!NOTE]
>  Se il nodo **Strumenti di database** non è visibile, selezionare **Mostra tutte le impostazioni**.  
  
1.  Fare clic su **Object Relational Designer**.  
  
2.  Impostare **pluralizzazione di nomi** al **Enabled** = **False** per impostare il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] in modo che non modifica i nomi delle classi.  
  
3.  Impostare **pluralizzazione di nomi** al **Enabled** = **True** per applicare le regole di pluralizzazione ai nomi di classe di oggetti aggiunti al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
