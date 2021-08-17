---
title: Panoramica delle proprietà dei documenti personalizzati
description: Si apprenderà che quando si compila un progetto a livello di documento, Visual Studio due proprietà personalizzate al documento nel progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a7b8b30304ed840843818a4d576fdfdb49bc36b54e72f77f441e1d9864e876c0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424437"
---
# <a name="custom-document-properties-overview"></a>Panoramica delle proprietà dei documenti personalizzati

Quando si compila un progetto a livello di documento, Visual Studio due proprietà personalizzate al documento nel progetto: \_ AssemblyLocation e \_ AssemblyName. Quando un utente apre un documento, l'applicazione Microsoft Office verifica la presenza di queste proprietà personalizzate del documento. Se sono presenti nel documento, l'applicazione carica [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , che avvia la personalizzazione. Per altre informazioni, vedere [Architecture of Office solutions in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_Assemblyname

Questa proprietà contiene il CLSID di un'interfaccia nel Office del caricatore della soluzione di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Il valore CLSID è 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B. Questo valore non deve mai essere modificato.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Questa proprietà contiene una stringa che fornisce informazioni dettagliate sul manifesto di distribuzione per la personalizzazione. Per altre informazioni sui manifesti, vedere [Manifesti dell'applicazione](../vsto/application-and-deployment-manifests-in-office-solutions.md)e della distribuzione in Office soluzioni .

 Il \_ valore della proprietà AssemblyLocation può avere formati diversi, a seconda della modalità di distribuzione della soluzione:

- Se la soluzione viene pubblicata per essere installata da un sito Web, da un percorso UNC o da un'unità CD o USB, la proprietà _AssemblyLocation ha il formato *DeploymentManifestPath* | *SolutionID*. La stringa seguente è un esempio:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Se si esegue o si esegue il debug della soluzione da Visual Studio, la proprietà _AssemblyLocation ha il formato *DeploymentManifestName* | *SolutionID*|vstolocal. La stringa seguente è un esempio:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

  *SolutionID* è un GUID utilizzato [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dall'oggetto per identificare la soluzione. SolutionID *viene* generato automaticamente quando si compila il progetto. Il **termine vstolocal** indica a che [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] l'assembly deve essere caricato dalla stessa cartella del documento.

## <a name="see-also"></a>Vedi anche

- [Architettura delle Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Manifesti dell'applicazione e della distribuzione Office soluzioni](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Procedura: Pubblicare una soluzione Office usando ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Procedura: Creare e modificare proprietà personalizzate del documento](../vsto/how-to-create-and-modify-custom-document-properties.md)