---
title: Elemento PreviewImage (modelli Visual Studio) | Microsoft Docs
description: Informazioni sull'elemento PreviewImage e su come specifica il nome file per l'immagine di anteprima che verrà visualizzata nella finestra di dialogo Nuovo Project o Aggiungi nuovo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a0ddae8f246ccedb6ca004743e7e18c22b38a0ddb4dabb671d55f07140274074
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431591"
---
# <a name="previewimage-element-visual-studio-templates"></a>Elemento PreviewImage (Visual Studio modelli)
Specifica l'immagine di anteprima, come nome file, per l'immagine di anteprima che verrà visualizzata nella finestra di dialogo **Nuovo Project** **o** Aggiungi nuovo elemento.

 \<VSTemplate> \<TemplateData>
 \<PreviewImage>

## <a name="syntax"></a>Sintassi

```
<PreviewImage>"filename"</PreviewImage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Categorizza il modello e definisce come viene visualizzato nella finestra di dialogo Nuovo **Project** o Aggiungi **nuovo** elemento.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere una stringa che rappresenta un nome file.

## <a name="remarks"></a>Commenti
 `PreviewImage` è un elemento facoltativo.

## <a name="see-also"></a>Vedi anche
- [Visual Studio riferimento allo schema del modello](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetto ed elemento](../ide/creating-project-and-item-templates.md)
