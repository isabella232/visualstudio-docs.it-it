---
title: Elemento AppliesTo (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f14924ac9464cc6239564f775a122551a9d94c15
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843645"
---
# <a name="appliesto-element-visual-studio-templates"></a>Elemento AppliesTo (modelli di Visual Studio)

Specifica un'espressione facoltativa in modo che corrisponda a uno o più funzionalità (vedere <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>). Le funzionalità esposte da tipi di progetto tramite la gerarchia come una proprietà [__VSHPROPID5. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). In questo modo, il modello può essere condiviso da molteplici tipi di progetto che dispongono di funzionalità applicabili comuni.

Questo elemento è facoltativo. Può essere presente massimo una istanza in un file modello. Questo elemento consente di includere come applicabile solo un modello di elemento, in base alle funzionalità del progetto attivo correntemente selezionato. Non può essere usato per rendere un modello di elemento non applicabile. Se `AppliesTo` è assente o l'espressione non è inclusa correttamente, viene usato `TemplateID` o `TemplateGroupID` per rendere il modello applicabile, come con le versioni precedenti del prodotto.

Introdotto in Visual Studio 2013 Update 2. Per correlare la versione corretta, vedere [riferimenti ad assembly recapitati in Visual Studio 2013 SDK Update 2](/previous-versions/dn632168(v=vs.120)).

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Sintassi

```xml
<AppliesTo>Capability1</AppliesTo>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria.|

## <a name="text-value"></a>Valore di testo

È necessario specificare un valore di testo. Questo testo specifica le funzionalità del progetto.

La sintassi valida dell'espressione è definita come segue:

- L'espressione della funzionalità, ad esempio "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".

- Il "&#124;" è l'operatore OR.

- Il "&" e "+" caratteri sono entrambi operatori AND.

- Il carattere "!" è l'operatore NOT.

- Le parentesi forzano l'ordine di precedenza nella valutazione.

- Un valore null o un'espressione vuota viene valutata come una corrispondenza.

- Le funzionalità del progetto possono essere qualsiasi carattere eccetto i caratteri riservati: "' :;,+-*/\\! ~&#124;& %$@^() ={}<> []? \t\b\n\r

## <a name="example"></a>Esempio

Nell'esempio seguente vengono mostrati tre diversi modelli. `Template1` si applica a tutti i tipi di progetto C# o a qualsiasi altro tipo di progetto che supporta la funzionalità `WindowsAppContainer`. `Template2` si applica a tutti i progetti C# di qualsiasi genere. `Template3` si applica a tutti i progetti C# che non sono progetti `WindowsAppContainer`.

```xml
<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 2 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>
    </TemplateData>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche

- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)