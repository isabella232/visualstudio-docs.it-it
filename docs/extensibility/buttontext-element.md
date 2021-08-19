---
title: Elemento ButtonText | Microsoft Docs
description: L'elemento ButtonText consente di specificare il testo visualizzato in vari menu. L'elemento ButtonText non può essere vuoto anche se sono specificati altri campi di testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f45a97ca24d61554e5901ed0322e49696dd5375c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133349"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Questo campo consente di specificare il testo visualizzato in vari menu. Per impostazione predefinita, `ButtonText` l'elemento viene visualizzato nei controller di menu. `ButtonText`L'elemento diventa l'impostazione predefinita anche se gli altri campi di testo sono vuoti. `ButtonText`L'elemento non può essere vuoto anche se vengono specificati gli altri campi di testo.

## <a name="syntax"></a>Sintassi

```xml
<ButtonText>My Command</ButtonText>
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
|[Elemento Strings](../extensibility/strings-element.md)|Raggruppa gli elementi di testo, ad `ButtonText` esempio e `CommandName` .|

## <a name="text-value"></a>Valore di testo
 Il valore di testo dell'elemento fornisce il testo visualizzato per le voci di menu, le combinazioni e altri elementi dell'interfaccia utente con `ButtonText` testo visibile.

## <a name="see-also"></a>Vedi anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
