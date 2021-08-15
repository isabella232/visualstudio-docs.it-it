---
title: Procedura guidata (. Vsz) File | Microsoft Docs
description: Informazioni sui file vsz utilizzati dall'IDE per avviare le procedure guidate. I file contengono informazioni sulla procedura guidata da chiamare e su cosa passare alla procedura guidata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 716ac3ce08b51695219b5c8cd33f49134f33d3626943e02c939c7427920f6e87
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121261125"
---
# <a name="wizard-vsz-file"></a>File (con estensione vsz) della procedura guidata

L'ambiente di sviluppo integrato (IDE) usa i file vsz per avviare le procedure guidate. Questi file vsz contengono informazioni utilizzate dall'IDE per determinare quale procedura guidata chiamare e quali informazioni passare alla procedura guidata.

Un file vsz è una versione di un .ini di testo in formato non in sezione. Le informazioni note all'IDE vengono archiviate all'inizio del file. In questo modo viene fornito un collegamento tra la procedura guidata chiamata dall'IDE e i parametri presenti nel file vsz da passare all'IDE. Il resto del file fornisce parametri specifici della procedura guidata che devono essere raccolti dall'IDE e passati alla procedura guidata specifica.

Nell'esempio seguente viene illustrato il contenuto di un file vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Di seguito sono riportate le parti nel file vsz.

|Parte|Descrizione|
|----------|-----------------|
|Vswizard|Il primo parametro nel file è il numero di versione del formato del file modello. Questo numero di versione deve essere 6.0, 7.0, 7.1 o 8.0. Gli altri numeri non possono essere avviati e causano un errore di formato non valido.|
|Procedura guidata|Questo campo contiene il ProgID OLE della procedura guidata o in alternativa una rappresentazione di stringa GUID del CLSID della procedura guidata cocreata dall'IDE.|
|Param|Queste parti sono facoltative. È possibile aggiungere il numero necessario.|

I parametri consentono al file vsz di passare parametri personalizzati aggiuntivi alla procedura guidata. Ogni valore viene passato come elemento stringa in una matrice di varianti alla procedura guidata. Per altre informazioni, vedere [Parametri personalizzati](../../extensibility/internals/custom-parameters.md).

Per aggiungere un ID impostazioni locali predefinito al file con estensione vsz, specificare =xxxx, dove xxxx è l'ID delle impostazioni locali, ad esempio `FALLBACK_LCID` 1033 per l'inglese. Quando il parametro è definito, la procedura guidata usa l'ID delle impostazioni locali di fallback fornito `FALLBACK_LCID` se l'ID corrente non viene trovato.

## <a name="see-also"></a>Vedi anche

- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
