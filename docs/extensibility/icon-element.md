---
title: Elemento Icon | Microsoft Docs
description: Informazioni sull'elemento Icon, che rappresenta le icone usate nelle estensioni IDE Visual Studio, che include gli attributi per la bitmap usata e lo slot nella striscia della bitmap.
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
ms.openlocfilehash: 26f942461a8d9be31e7802fb63f0249b69046663
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070204"
---
# <a name="icon-element"></a>Elemento Icon
L'attributo guid del tag Icon è il GUID di una bitmap definita. `id`L'attributo seleziona lo slot nella striscia bitmap. Questo elemento è facoltativo. Se questo elemento non è incluso, verrà implicito il valore di **guidOfficeIcon:msotcidNoIcon.**

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
|id|Obbligatorio. Seleziona lo slot nella striscia bitmap.|

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
