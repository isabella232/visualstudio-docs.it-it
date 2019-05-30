---
title: Elemento PreviewImage (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86ed3e6f438f399547996245531c2848ac7bdb83
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336083"
---
# <a name="previewimage-element-visual-studio-templates"></a>Elemento PreviewImage (modelli di Visual Studio)
Specifica l'immagine di anteprima, come un nome di file, per l'immagine di anteprima che verrà visualizzato in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** nella finestra di dialogo.

 \<VSTemplate> \<TemplateData> \<PreviewImage>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce come viene visualizzato in entrambi i **nuovo progetto** o il **Aggiungi nuovo elemento** nella finestra di dialogo.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo deve essere una stringa che rappresenta un nome di file.

## <a name="remarks"></a>Note
 `PreviewImage` è un elemento facoltativo.

## <a name="see-also"></a>Vedere anche
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)