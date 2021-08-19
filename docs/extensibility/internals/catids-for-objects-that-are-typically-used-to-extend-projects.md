---
title: CATID per gli oggetti usati in genere per estendere i progetti
description: Informazioni sui CATID per gli oggetti usati per estendere gli oggetti di automazione Project e ProjectItem per Visual Basic, Visual C# e Visual C++ progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 04253f9bfe45cd893ecbf1401fc9d7e12391a4c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159204"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATID per oggetti usati in genere per estendere i progetti
Nella tabella seguente sono elencati i CATID utilizzati per estendere e gli oggetti `Project` `ProjectItem` di automazione per i progetti [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] , e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . Questi CATID sono definiti in *VSLangProj.olb.*

## <a name="listing-of-catids"></a>Elenco dei CATID

|Nome|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>Visual Basic CATID
 Nella tabella seguente sono elencati i CATID utilizzati per estendere gli [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oggetti di esplorazione. Sono tutti definiti in *VSLangProj.olb.*

|Nome|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>CATID di Visual C#
 I CATID seguenti possono essere usati per estendere gli [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] oggetti di esplorazione. Sono tutti definiti in *VSLangProj.olb.*

|Nome|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>CATID C++
 I CATID del sistema di progetto seguenti non sono esposti nelle librerie dei tipi [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] in .NET 2003 e devono essere inclusi nel codice ogni volta che si vogliono estendere questi oggetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di progetto. Questi CATID verranno inclusi nelle librerie dei tipi nelle versioni successive di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Nome|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 L'esempio di codice seguente illustra come programmare questi CATID nel codice.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Anche i CATID del sistema di progetto seguenti non sono esposti nelle librerie dei tipi [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] in .NET 2003 e devono essere inclusi nel codice ogni volta che si vogliono estendere questi oggetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di progetto. Questi CATID sono disponibili solo in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 e non saranno disponibili nelle versioni successive di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Nome|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 L'esempio di codice seguente illustra come programmare questi CATID nel codice:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 I GUID per i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tipi di progetto e sono illustrati nella tabella [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] seguente.

| Tipo di progetto | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>Vedi anche
- [Aggiungere modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Registrare modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)
