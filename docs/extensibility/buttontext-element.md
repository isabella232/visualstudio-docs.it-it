---
title: Elemento ButtonText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe2440258e95ad0d61998b24dae54b731a998c47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321223"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Questo campo consente di specificare il testo visualizzato nei vari menu. Per impostazione predefinita, il `ButtonText` elemento compare in un controller di menu. Il `ButtonText` elemento diventa l'impostazione predefinita anche se gli altri campi di testo sono vuoti. Il `ButtonText` elemento non può essere vuoto anche se vengono specificati gli altri campi di testo.

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
|[Elemento Strings](../extensibility/strings-element.md)|Raggruppa gli elementi di testo, ad esempio `ButtonText` e `CommandName`.|

## <a name="text-value"></a>Valore di testo
 Il valore del testo di `ButtonText` elemento fornisce il testo visualizzato per le voci di menu, combos e altri elementi dell'interfaccia utente con testo visibile.

## <a name="see-also"></a>Vedere anche
- [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)