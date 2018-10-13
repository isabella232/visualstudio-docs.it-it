---
title: 'Procedura: estendere il codice generato dalla finestra di progettazione O-R | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 14fd1f950d50f2cb71e56fc8b1e75ff60f3da0ce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227919"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Procedura: estendere il codice generato da O/R Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Il codice generato da [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] viene rigenerato quando vengono apportate modifiche alle classi di entità e ad altri oggetti nell'area di progettazione. A causa di questa rigenerazione, in genere tutto il codice aggiunto al codice generato viene sovrascritto quando la finestra di progettazione rigenera il codice. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] offre la possibilità di generare file di classe parziale in cui è possibile aggiungere codice che non verrà sovrascritto. Un esempio di aggiunta di codice personalizzato al codice generato da [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] consiste nell'aggiungere la convalida di dati a classi (di entità) LINQ to SQL. Per informazioni, vedere [procedura: aggiungere la convalida a classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Aggiunta di codice a una classe di entità  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Per creare una classe parziale e aggiungere codice a una classe di entità  
  
1.  Aprire o creare un nuovo file LINQ to SQL classi (**dbml** file) nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Fare doppio clic il **dbml** del file in **Esplora soluzioni**/**Esplora Database**.)  
  
2.  Nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], fare doppio clic su della classe per cui si desidera aggiungere la convalida e quindi fare clic su **Visualizza codice**.  
  
     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.  
  
3.  Aggiungere il codice nella dichiarazione di classe parziale per la classe di entità.  
  
## <a name="adding-code-to-a-datacontext"></a>Aggiunta di codice a un oggetto DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Per creare una classe parziale e aggiungere codice a un oggetto DataContext  
  
1.  Aprire o creare un nuovo file LINQ to SQL classi (**dbml** file) nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Fare doppio clic il **dbml** del file in **Esplora soluzioni**/**Esplora Database**.)  
  
2.  Nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], fare doppio clic su un'area vuota della finestra di progettazione e quindi fare clic su **Visualizza codice**.  
  
     Viene aperto l'editor del codice con una classe parziale per l'oggetto DataContext.  
  
3.  Aggiungere il codice nella dichiarazione di classe parziale per l'oggetto DataContext.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Procedura dettagliata: Aggiunta della convalida alle classi di entità](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)

