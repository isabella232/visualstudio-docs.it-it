---
title: 'Procedura: aprire soluzioni Office senza eseguire il codice | Documenti Microsoft'
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
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c190c4ace56b2be9c63c9f11570354cddc6c8635
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Procedura: aprire soluzioni Office senza eseguire codice
  Una soluzione Microsoft Office creata con le estensioni di codice gestito viene eseguito anche se l'impostazione di sicurezza nell'applicazione Office dell'utente finale viene impostata su alto. In questo modo la sicurezza di codice assembly .NET è gestita da Microsoft .NET Framework, non da Microsoft Office.  
  
 Tuttavia, esistono volte quando si potrebbe desiderare di aprire un documento senza eseguire il codice. Ad esempio, il codice eseguito all'apertura del documento potrebbe alterare il contenuto, ma si desidera aggiornare l'aspetto il documento prima di modifiche del codice è. O è utile inviare il documento con determinate informazioni a un utente, e non si desidera il codice da eseguire ed eventualmente modificare il contenuto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Esistono diversi modi per aprire un documento o una cartella di lavoro che contiene le estensioni di codice gestito senza eseguire il codice dell'assembly.  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Per ignorare l'assembly utilizzando il tasto MAIUSC  
  
-   Aprire i documenti e cartelle di lavoro di **File** menu tenendo premuto il tasto MAIUSC per impedire la generazione di eventi di inizializzazione, mentre è aperto il documento di Word ed Excel.  
  
    > [!NOTE]  
    >  Se si apre un documento o una cartella di lavoro dal **Introduzione** riquadro attività, tenere premuto MAIUSC il codice viene ignorato. Inoltre, tenere premuto MAIUSC non impedisce gli eventi viene generato dopo che il documento è aperto.  
  
     Questo metodo è utile se si desidera aprire un documento per apportare modifiche senza che il codice in esecuzione e la modifica prima di tutto il documento.  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Per ignorare la ridenominazione o rimozione un assembly  
  
-   Se si dispone delle autorizzazioni necessarie nel computer in cui si trova l'assembly, è possibile rinominare o rimuovere l'assembly in modo che il documento o la cartella di lavoro non riesce a trovarla. Ciò comporta un errore viene generato ogni volta che viene aperto il documento di Office.  
  
     Se la soluzione viene utilizzata da più utenti, questo metodo impedisce in esecuzione per tutti gli elementi della soluzione. Può essere utile se viene rilevato un problema nel codice o un server di riferimento e si desidera arrestare tutti gli utenti di eseguirlo.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  