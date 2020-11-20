---
title: Elemento ButtonText | Microsoft Docs
description: L'elemento ButtonText consente di specificare il testo visualizzato in vari menu. L'elemento ButtonText non può essere vuoto anche se sono specificati altri campi di testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2db20bb3298a7b849e8bc4a261987c5314a29841
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974473"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Questo campo consente di specificare il testo visualizzato in vari menu. Per impostazione predefinita, l' `ButtonText` elemento viene visualizzato nei controller di menu. L' `ButtonText` elemento diventa anche il valore predefinito se gli altri campi di testo sono vuoti. L' `ButtonText` elemento non può essere vuoto anche se gli altri campi di testo sono specificati.

## <a name="syntax"></a>Sintassi

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi
 No.

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Strings](../extensibility/strings-element.md)|Raggruppa gli elementi di testo, ad esempio `ButtonText` e `CommandName` .|

## <a name="text-value"></a>Valore di testo
 Il valore di testo dell' `ButtonText` elemento fornisce il testo visualizzato per le voci di menu, le combinazioni e altri elementi dell'interfaccia utente con testo visibile.

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
