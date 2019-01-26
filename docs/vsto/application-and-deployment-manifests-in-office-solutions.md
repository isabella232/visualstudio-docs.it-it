---
title: Manifesti dell'applicazione e distribuzione nelle soluzioni Office
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9deabada5a9e3d69c3d3a9a821abf7d6b8dcf56e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875615"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifesti dell'applicazione e distribuzione nelle soluzioni Office
  Un manifesto dell'applicazione è un file XML che fornisce informazioni usate da una soluzione Office per individuare e aggiornare i relativi assembly. Un manifesto dell'applicazione può essere usato con un manifesto di distribuzione, costituito da un file XML archiviato nel server, che fornisce le informazioni necessarie per individuare la versione più recente del manifesto dell'applicazione e degli assembly.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Struttura del manifesto per le soluzioni Office
 Per le soluzioni Microsoft Office create tramite gli strumenti di sviluppo di Office in Visual Studio, tutti i manifesti sono basati sullo schema ClickOnce standard. Quando si distribuiscono le soluzioni Office, i manifesti dell'applicazione per i progetti di componente aggiuntivo VSTO e a livello di documento si trovano nella cache di ClickOnce. I manifesti di distribuzione non vengono copiati nel computer client.

 Per informazioni sui contenuti dei manifesti dell'applicazione e distribuzione per progetti di Office, vedere [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md) e [manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Creazione di manifesti dell'applicazione e distribuzione
 I manifesti dell'applicazione vengono creati automaticamente come parte del processo di compilazione. Ogni volta che si compila un progetto a livello di documento, il percorso del manifesto di distribuzione è incorporato nel documento come proprietà personalizzata del documento. Per i componenti aggiuntivi VSTO, il percorso del manifesto della distribuzione è archiviato nel registro di sistema.

 Per altre informazioni sul **pubblicazione guidata**, vedere [distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Per altre informazioni su come dei manifesti con soluzioni Office, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedere anche

- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Progettare e creare soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
- [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)