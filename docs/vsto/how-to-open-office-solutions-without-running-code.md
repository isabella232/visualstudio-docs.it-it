---
title: 'Procedura: Aprire soluzioni Office senza eseguire codice'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 59cee99ad603ec1a03f8beffd36b82d4b83ed308
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930106"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Procedura: Aprire soluzioni Office senza eseguire codice
  Una soluzione di Microsoft Office creata con le estensioni di codice gestito viene eseguito anche se l'impostazione di sicurezza nell'applicazione Office dell'utente finale è impostato sul livello più alto. Questo avviene perché la protezione di codice degli assembly .NET è gestita da Microsoft .NET Framework, non da Microsoft Office.  
  
 Tuttavia, esistono volte quando si potrebbe desiderare di aprire un documento senza eseguire il codice. Ad esempio, il codice eseguito all'apertura del documento potrebbe alterare il contenuto, ma si desidera aggiornare l'aspetto il documento prima le modifiche al codice è. Oppure si potrebbe voler inviare il documento con determinate informazioni in esso a un utente e non si desidera il codice per eseguire e possibilmente modificare il contenuto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Esistono diversi modi per aprire un documento o cartella di lavoro che contiene le estensioni di codice gestito senza eseguire il codice dell'assembly.  
  
## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Per ignorare l'assembly usando il tasto MAIUSC  
  
-   Aprire i documenti e cartelle di lavoro dei **File** menu tenendo premuto il **MAIUSC** chiave per impedire la generazione di eventi di inizializzazione mentre è aperto il documento di Word ed Excel.  
  
    > [!NOTE]  
    >  Se si apre un documento o una cartella di lavoro dal **Guida introduttiva** riquadro attività, tenendo premuto **MAIUSC** non bypassano il codice. Inoltre, tenendo premuto MAIUSC non impedisce gli eventi generati dopo aver aperto il documento.  
  
     Questo metodo è utile se si desidera aprire un documento per apportare modifiche senza che il codice in esecuzione e la modifica prima di tutto il documento.  
  
## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Per ignorare un assembly, è possibile rinominare o rimuoverlo  
  
-   Se si dispone delle autorizzazioni necessarie nel computer in cui si trova l'assembly, è possibile rinominare o rimuovere l'assembly in modo che il documento o la cartella di lavoro non riesce a trovarla. Ciò comporta un errore viene generato ogni volta che viene aperto il documento di Office.  
  
     Se la soluzione viene usata da più persone, questo metodo impedisce la soluzione di esecuzione per tutti gli elementi. Ciò può essere utile se viene rilevato un problema nel codice o un server di riferimento e si vuole arrestare tutti gli utenti di eseguirlo.  
  
## <a name="see-also"></a>Vedere anche  
 [Proteggere le soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifesti dell'applicazione e distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
