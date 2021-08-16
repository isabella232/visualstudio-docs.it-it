---
title: Elemento Icon | Microsoft Docs
description: Informazioni sull'elemento Icon, che rappresenta le icone usate Visual Studio estensioni IDE, che include gli attributi per la bitmap usata e lo slot nella striscia di bitmap.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 861bca1bc4a0f43f8e5165ae4fdf172fc858dfaf575683a921f52f3428e9c0d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414675"
---
# <a name="icon-element"></a>Elemento Icon
L'attributo guid del tag Icon è il GUID di una bitmap definita. `id`L'attributo seleziona lo slot nell'elenco di bitmap. Questo elemento è facoltativo. Se questo elemento non è incluso, verrà implicito il valore di **guidOfficeIcon:msotcidNoIcon.**

## <a name="syntax"></a>Sintassi

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID di una bitmap definita.|
|id|Obbligatorio. Seleziona lo slot nell'elenco di bitmap.|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|No.|No.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Vedi anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
