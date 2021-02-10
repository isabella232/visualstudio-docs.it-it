---
title: Cenni preliminari sulle proprietà personalizzate del documento
description: Quando si compila un progetto a livello di documento, Visual Studio aggiunge due proprietà personalizzate al documento nel progetto.
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
ms.workload:
- office
ms.openlocfilehash: 51039c71c97614cb9e43df263b3d7155c9cb86f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947801"
---
# <a name="custom-document-properties-overview"></a>Cenni preliminari sulle proprietà personalizzate del documento

Quando si compila un progetto a livello di documento, Visual Studio aggiunge due proprietà personalizzate al documento nel progetto: \_ PercorsoAssembly e \_ AssemblyName. Quando un utente apre un documento, l'applicazione Microsoft Office controlla le proprietà personalizzate del documento. Se sono presenti nel documento, l'applicazione carica [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , che avvia la personalizzazione. Per altre informazioni, vedere [architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_AssemblyName

Questa proprietà contiene il CLSID di un'interfaccia nel componente del caricatore di soluzioni Office dell'oggetto [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Il valore CLSID è 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B. Questo valore non deve mai essere modificato.

## <a name="_assemblylocation"></a>\_PercorsoAssembly

Questa proprietà contiene una stringa che fornisce informazioni dettagliate sul manifesto di distribuzione per la personalizzazione. Per altre informazioni sui manifesti, vedere [manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Il \_ valore della proprietà PercorsoAssembly può avere formati diversi, a seconda della modalità di distribuzione della soluzione:

- Se la soluzione è pubblicata per essere installata da un sito Web, da un percorso UNC o da un'unità CD o USB, il formato della proprietà _AssemblyLocation è *DeploymentManifestPath* | *SolutionID*. La stringa seguente è un esempio:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Se si esegue o si esegue il debug della soluzione da Visual Studio, la proprietà _AssemblyLocation ha il formato *DeploymentManifestName* | *SolutionID*| vstolocal. La stringa seguente è un esempio:

     ExcelWorkbook1. VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  *SolutionID* è un GUID [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usato da per identificare la soluzione. Il *SolutionID* viene generato automaticamente quando si compila il progetto. Il termine **vstolocal** indica a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che l'assembly deve essere caricato dalla stessa cartella del documento.

## <a name="see-also"></a>Vedi anche

- [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Procedura: pubblicare una soluzione Office tramite ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Procedura: creare e modificare proprietà personalizzate di un documento](../vsto/how-to-create-and-modify-custom-document-properties.md)