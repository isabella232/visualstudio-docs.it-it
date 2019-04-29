---
title: Elemento CustomDataSignature (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96c8431ec6382c19e5f771d92e4fe7d07d68ea4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926367"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Elemento CustomDataSignature (modelli di Visual Studio)
Specifica la firma di testo per individuare i dati personalizzati.

 \<VSTemplate > \<TemplateData > \<CustomDataSignature >

## <a name="syntax"></a>Sintassi

```
<CustomDataSignature>"string"</CustomDataSignature>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce come viene visualizzato in entrambi i **nuovo progetto** o il **Aggiungi nuovo elemento** nella finestra di dialogo.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo è una stringa con la firma di testo che è necessario per individuare i dati personalizzati.

## <a name="remarks"></a>Note
 `CustomDataSignature` è un elemento facoltativo.

## <a name="see-also"></a>Vedere anche
- [Riferimenti allo schema di Visual Studio modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)