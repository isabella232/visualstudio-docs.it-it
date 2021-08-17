---
title: 'Procedura: Aprire soluzioni Office senza eseguire codice'
description: Informazioni su come aprire un documento o una cartella di lavoro che contiene estensioni di codice gestito senza eseguire il codice assembly.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b7816072d0cb5ee55c753eea4e1d0bdf2e8bafe1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026238"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Procedura: Aprire soluzioni Office senza eseguire codice
  Una Microsoft Office creata con estensioni di codice gestito viene eseguita anche se l'impostazione Sicurezza nell'applicazione Office dell'utente finale è impostata su Alta. Ciò è dovuto al fatto che la sicurezza del codice assembly .NET è gestita da Microsoft .NET Framework, non da Microsoft Office.

 Tuttavia, in alcuni casi potrebbe essere necessario aprire un documento senza eseguire il codice. Ad esempio, il codice eseguito all'apertura del documento potrebbe modificare il contenuto, ma si vuole aggiornare l'aspetto del documento prima che venga modificato dal codice. In caso contrario, è possibile inviare il documento con determinate informazioni a un utente e non si vuole che il codice venga eseguito ed eventualmente modificare il contenuto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Esistono diversi modi per aprire un documento o una cartella di lavoro che contiene estensioni di codice gestito senza eseguire il codice assembly.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Per ignorare l'assembly usando il tasto MAIUSC

- Aprire documenti e cartelle di lavoro dal  menu **File** tenendo premuto MAIUSC per impedire a Word e Excel di generare eventi di inizializzazione durante l'apertura del documento.

    > [!NOTE]
    > Se si apre un documento o una cartella di lavoro **dal** riquadro Attività iniziali attività, tenendo premuto **MAIUSC** non viene ignorato il codice. Inoltre, tenendo premuto MAIUSC, gli eventi non vengono generati dopo l'apertura del documento.

     Questo metodo è utile se si vuole aprire un documento per apportare modifiche senza prima eseguire il codice e modificare il documento.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Per ignorare un assembly rinominandolo o rimuovendolo

- Se si dispone delle autorizzazioni necessarie nel computer in cui si trova l'assembly, è possibile rinominare o rimuovere l'assembly in modo che il documento o la cartella di lavoro non possa trovarlo. Viene generato un errore ogni volta che viene aperto Office documento.

     Se la soluzione viene usata da più utenti, questo metodo impedisce l'esecuzione della soluzione per tutti gli utenti. Ciò può essere utile se viene rilevato un problema nel codice o in un server di riferimento e si vuole impedire a tutti gli utenti di eseguirlo.

## <a name="see-also"></a>Vedi anche
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Manifesti dell'applicazione e della distribuzione Office soluzioni](../vsto/application-and-deployment-manifests-in-office-solutions.md)
