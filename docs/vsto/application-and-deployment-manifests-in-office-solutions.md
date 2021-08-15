---
title: Manifesti dell'applicazione e della distribuzione in Office soluzioni
description: Informazioni su come un manifesto dell'applicazione è un file XML che fornisce informazioni usate da una soluzione Office per individuare e aggiornare gli assembly.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 17ff7893ddf4961f6271d4e6ebf285faeb771c528f52d7b5ff14c1147cd81097
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121299045"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifesti dell'applicazione e della distribuzione in Office soluzioni
  Un manifesto dell'applicazione è un file XML che fornisce informazioni usate da una soluzione Office per individuare e aggiornare i relativi assembly. Un manifesto dell'applicazione può essere usato con un manifesto di distribuzione, costituito da un file XML archiviato nel server, che fornisce le informazioni necessarie per individuare la versione più recente del manifesto dell'applicazione e degli assembly.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Struttura del manifesto per Office soluzioni
 Per le soluzioni Microsoft Office create tramite gli strumenti di sviluppo di Office in Visual Studio, tutti i manifesti sono basati sullo schema ClickOnce standard. Quando si distribuiscono le soluzioni Office, i manifesti dell'applicazione per i progetti di componente aggiuntivo VSTO e a livello di documento si trovano nella cache di ClickOnce. I manifesti di distribuzione non vengono copiati nel computer client.

 Per informazioni sul contenuto dei manifesti dell'applicazione e [](../vsto/application-manifests-for-office-solutions.md) della distribuzione per Office, vedere Manifesti dell'applicazione per le soluzioni Office e Manifesti di distribuzione per Office [soluzioni](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Creare manifesti dell'applicazione e della distribuzione
 I manifesti dell'applicazione vengono creati automaticamente come parte del processo di compilazione. Ogni volta che si compila un progetto a livello di documento, il percorso del manifesto di distribuzione è incorporato nel documento come proprietà personalizzata del documento. Per i componenti aggiuntivi VSTO, il percorso del manifesto della distribuzione è archiviato nel registro di sistema.

 Per altre informazioni sulla **Pubblicazione guidata,** vedere [Deploy an Office solution by using ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Per altre informazioni sul funzionamento dei manifesti con Office soluzioni, vedere [Distribuire una Office soluzione](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedi anche

- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
- [ClickOnce manifesto della distribuzione](../deployment/clickonce-deployment-manifest.md)