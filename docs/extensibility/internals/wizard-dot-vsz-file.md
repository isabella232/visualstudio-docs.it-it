---
title: Procedura guidata (. Vsz) File Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fedf409c0ca320c054ddf1cc16318d08d25463a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703315"
---
# <a name="wizard-vsz-file"></a>File (con estensione vsz) della procedura guidata

L'ambiente di sviluppo integrato (IDE) utilizza i file vsz per avviare le procedure guidate. Questi file vsz contengono informazioni che l'IDE utilizza per determinare quale procedura guidata chiamare e quali informazioni passare alla procedura guidata.

Un file vsz è una versione di un file di testo in formato .ini che non ha sezioni. Le informazioni note all'IDE vengono archiviate all'inizio del file. In questo modo viene fornito un collegamento tra la procedura guidata chiamata dall'IDE e i parametri presenti nel file vsz da passare all'IDE. Il resto del file fornisce parametri specifici per la procedura guidata e che devono essere raccolti dall'IDE e passati alla procedura guidata specifica.

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
|Vswizard|Il primo parametro nel file è il numero di versione del formato di file modello. Questo numero di versione deve essere 6.0, 7.0, 7.1 o 8.0.This version number must be 6.0, 7.0, 7.1 or 8.0. Altri numeri non possono essere avviati e causano un errore di formato non valido.|
|Procedura guidata|Questo campo contiene il ProgID OLE della procedura guidata o, in alternativa, una rappresentazione di stringa GUID del CLSID della procedura guidata cocreata dall'IDE.|
|Param|Queste parti sono facoltative. È possibile aggiungere il numero necessario.|

I parametri consentono al file vsz di passare parametri personalizzati aggiuntivi alla procedura guidata. Ogni valore viene passato come elemento stringa in una matrice di varianti alla procedura guidata. Per ulteriori informazioni, vedere [Parametri personalizzati](../../extensibility/internals/custom-parameters.md).

Per aggiungere un ID delle impostazioni locali `FALLBACK_LCID`predefinito al file vsz, specificare xxxx, dove xxxx è l'ID delle impostazioni locali, ad esempio 1033 per l'inglese. Quando `FALLBACK_LCID` il parametro è definito, la procedura guidata utilizza l'ID delle impostazioni locali di fallback fornito se l'ID corrente non viene trovato.

## <a name="see-also"></a>Vedere anche

- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
