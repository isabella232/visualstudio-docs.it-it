---
title: Elemento RequiredPlatformVersion (modelli di Visual Studio)
titleSuffix: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3873a8107c60802edd07b567d65205a37dc213
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741684"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (modelli di Visual Studio)

Specifica la versione minima del sistema operativo necessaria per il corretto funzionamento del modello di progetto. Questo elemento viene usato per i modelli di progetto per la creazione di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.

 Il `RequiredPlatformVersion` valore viene confrontato direttamente con la versione del sistema operativo. Se `RequiredPlatformVersion` è superiore alla versione del sistema operativo, il modello non viene visualizzato nella finestra di dialogo **nuovo progetto** . Per specificare un modello per [!INCLUDE[win8](../debugger/includes/win8_md.md)] o versione successiva, impostare `RequiredPlatformVersion` su 6.2.0. Per specificare un modello per [!INCLUDE[win81](../debugger/includes/win81_md.md)] o versione successiva, impostare `RequiredPlatformVersion` su 6.3.0.

 I modelli che specificano `RequiredPlatformVersion` = 8 sono compatibili con i modelli di cliente precedenti [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] .

 TemplateData VSTemplate.... RequiredPlatformVersion TargetPlatformName

## <a name="syntax"></a>Sintassi

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nessuno.

### <a name="attributes"></a>Attributes

 Nessuno.

### <a name="child-elements"></a>Elementi figlio

 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Specifica la piattaforma a cui è destinato il modello di progetto.|

## <a name="text-value"></a>Valore di testo

 È necessario specificare un valore di testo.

## <a name="remarks"></a>Osservazioni

 Questo testo specifica la versione minima del sistema operativo richiesta dal modello.

## <a name="example"></a>Esempio

 Questo esempio specifica che il modello di progetto è destinato a [!INCLUDE[win8](../debugger/includes/win8_md.md)] o versioni successive.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vedere anche

- [Elemento TargetPlatformName (modelli di Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
