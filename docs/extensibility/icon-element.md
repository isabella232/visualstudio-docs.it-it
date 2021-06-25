---
title: Elemento Icon | Microsoft Docs
description: Informazioni sull'elemento Icon, che rappresenta le icone usate nelle Visual Studio IDE, che include gli attributi per la bitmap usata e lo slot nella striscia di bitmap.
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
ms.workload:
- vssdk
ms.openlocfilehash: 7ad5bfdf000232ef92a9e9a27b12152df36a4335
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900824"
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

## <a name="see-also"></a>Vedere anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
