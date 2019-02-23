---
title: Elemento TemplateGroupID (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9219b764125727509807cc6f2b9fdf6400e97f2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685248"
---
# <a name="templategroupid-element-visual-studio-templates"></a>Elemento TemplateGroupID (modelli di Visual Studio)
Specifica il tipo di progetto in cui verranno visualizzati i modelli di elemento. Questo elemento è significativo quando [ShowByDefault (modelli di Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) è impostata su `false`. Quando [ShowByDefault (modelli di Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) è impostata su `true`, un modello di elemento è disponibile in tutti i tipi di progetto.

 \<VSTemplate> \<TemplateData> \<TemplateGroupID>

## <a name="syntax"></a>Sintassi

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

 Il testo specifica un identificatore per una categoria di modelli di elemento.

## <a name="remarks"></a>Note
 `TemplateGroupID` è un elemento.

 Il valore della `TemplateGroupID` elemento viene usato con la registrazione nel sistema di progetto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<numero di versione >* \Projects\\) per i modelli di filtro che vengono visualizzati nei **Aggiungi nuovo elemento** nella finestra di dialogo.

|Valore di Visual C++|Significato|
|------------------------|-------------|
|VC-Native|Usato nei progetti nativi. È anche il valore predefinito se non è possibile determinare un tipo di progetto.|
|VC-Managed|Usato per i progetti (/clr) gestiti|
|VC-Windows|Usato per tutti i progetti per la piattaforma Windows (nativi/gestiti/Store)|
|WinRT-Native-UAP|Usato per i progetti Store di Windows 10|
|CodeSharing-Native|Usato per i progetti di elementi condivisi|
|WinRT-Native-6.3|Usato per i progetti Store di Windows 8.1|
|WinRT-Native-Phone-6.3|Usato per i progetti Windows Phone 8.1|
|WinRT-Nativo|Usato per i progetti Store di Windows 8.0|
|VC-Android|Usato per i progetti Android|

## <a name="see-also"></a>Vedere anche
- [Riferimenti sullo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)