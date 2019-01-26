---
title: Cenni preliminari sulle proprietà personalizzate dei documenti
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 11c344b683a67f369ef3848a41b7907622945ffa
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866857"
---
# <a name="custom-document-properties-overview"></a>Cenni preliminari sulle proprietà personalizzate dei documenti

Quando si compila un progetto a livello di documento, Visual Studio aggiunge due proprietà personalizzate per il documento nel progetto: \_AssemblyLocation e \_AssemblyName. Quando un utente apre un documento, l'applicazione Microsoft Office controlla per queste proprietà personalizzate dei documenti. Se sono presenti nel documento, l'applicazione carica il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], che avvia la personalizzazione. Per altre informazioni, vedere [soluzioni di architettura di Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Questa proprietà contiene il CLSID di un'interfaccia il caricatore di soluzioni Office del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Il valore CLSID è 4-491E-A7D4-64AF99AF6E8B 4E3C66D5 - 58D. Non è necessario modificare questo valore.

## <a name="assemblylocation"></a>\_AssemblyLocation

Questa proprietà contiene una stringa che fornisce dettagli sul manifesto di distribuzione per la personalizzazione. Per altre informazioni sui manifesti, vedere [i manifesti dell'applicazione e distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Il \_valore della proprietà AssemblyLocation può avere formati diversi, a seconda del modo in cui la soluzione viene distribuita:

- Se la soluzione viene pubblicata per essere installata da un sito Web, percorso UNC o una CD o unità USB, la proprietà AssemblyLocation ha il formato *DeploymentManifestPath*|*SolutionID*. La stringa seguente è riportato un esempio:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Se si sono in esecuzione o debug della soluzione da Visual Studio, la proprietà AssemblyLocation ha il formato *DeploymentManifestName*|*SolutionID*| vstolocal. La stringa seguente è riportato un esempio:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

  Il *SolutionID* è un GUID che il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene utilizzato per identificare la soluzione. Il *SolutionID* viene generato automaticamente quando si compila il progetto. Il **vstolocal** termine indica al [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che l'assembly deve essere caricato dalla stessa cartella del documento.

## <a name="see-also"></a>Vedere anche

- [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)
- [Manifesti dell'applicazione e distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Procedura: Distribuire una soluzione Office usando ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Procedura: Creare e modificare le proprietà personalizzate dei documenti](../vsto/how-to-create-and-modify-custom-document-properties.md)
