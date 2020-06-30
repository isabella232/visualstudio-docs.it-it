---
title: 'Procedura: aprire soluzioni Office senza eseguire codice'
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d84515c2c3159b61b96f77555b23eef0df0ae961
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543481"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Procedura: aprire soluzioni Office senza eseguire codice
  Una soluzione Microsoft Office creata con estensioni di codice gestito viene eseguita anche se l'impostazione di sicurezza nell'applicazione di Office dell'utente finale è impostata su alta. Questo è dovuto al fatto che la sicurezza del codice assembly .NET viene gestita dal framework di Microsoft .NET, non da Microsoft Office.

 In alcuni casi, tuttavia, potrebbe essere necessario aprire un documento senza eseguire il codice. Ad esempio, il codice che viene eseguito quando il documento viene aperto potrebbe modificare il contenuto, ma si desidera aggiornare il modo in cui il documento appare prima che il codice lo modifichi. In alternativa, è possibile inviare il documento con determinate informazioni a un utente e non si vuole che il codice venga eseguito ed eventualmente modifichi il contenuto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Esistono diversi modi per aprire un documento o una cartella di lavoro che contiene estensioni di codice gestito senza eseguire il codice dell'assembly.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Per ignorare l'assembly utilizzando il tasto MAIUSC

- Aprire documenti e cartelle di lavoro dal menu **file** tenendo premuto il tasto **MAIUSC** per impedire a Word ed Excel di generare eventi di inizializzazione durante l'apertura del documento.

    > [!NOTE]
    > Se si apre un documento o una cartella di lavoro dal riquadro attività **Introduzione** , tenere premuto **MAIUSC** non ignora il codice. Inoltre, tenere premuto MAIUSC non impedisce la generazione di eventi dopo l'apertura del documento.

     Questo metodo è utile se si desidera aprire un documento per apportare modifiche senza che il codice sia in esecuzione e modificare prima il documento.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Per ignorare un assembly rinominando o rimuovendo l'assembly

- Se si dispone delle autorizzazioni necessarie per il computer in cui si trova l'assembly, è possibile rinominare o rimuovere l'assembly in modo che il documento o la cartella di lavoro non lo trovino. Ciò comporta la generazione di un errore ogni volta che viene aperto il documento di Office.

     Se la soluzione viene utilizzata da più persone, questo metodo impedisce l'esecuzione della soluzione per tutti i membri. Questo può essere utile se si riscontra un problema nel codice o in un server a cui si fa riferimento e si desidera impedire a tutti gli utenti di eseguirlo.

## <a name="see-also"></a>Vedere anche
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
