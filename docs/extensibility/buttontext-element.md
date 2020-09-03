---
title: Elemento ButtonText | Microsoft Docs
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
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739912"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Questo campo consente di specificare il testo visualizzato in vari menu. Per impostazione predefinita, l' `ButtonText` elemento viene visualizzato nei controller di menu. L' `ButtonText` elemento diventa anche il valore predefinito se gli altri campi di testo sono vuoti. L' `ButtonText` elemento non può essere vuoto anche se gli altri campi di testo sono specificati.

## <a name="syntax"></a>Sintassi

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributes
 Nessuno.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Strings](../extensibility/strings-element.md)|Raggruppa gli elementi di testo, ad esempio `ButtonText` e `CommandName` .|

## <a name="text-value"></a>Valore di testo
 Il valore di testo dell' `ButtonText` elemento fornisce il testo visualizzato per le voci di menu, le combinazioni e altri elementi dell'interfaccia utente con testo visibile.

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
