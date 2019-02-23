---
title: Elemento RequiredPlatformVersion (modelli di Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73dcb29211eac35fad670f981aae1ebda75e2436
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716155"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (modelli di Visual Studio)
Specifica la versione minima del sistema operativo il modello di progetto necessaria per funzionare correttamente. Questo elemento viene usato per modelli di progetto che creano [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] app.

 Il `RequiredPlatformVersion` valore viene confrontato direttamente con la versione del sistema operativo. Se il `RequiredPlatformVersion` è superiore alla versione del sistema operativo, il modello non viene visualizzato nei **nuovo progetto** nella finestra di dialogo. Per specificare un modello per [!INCLUDE[win8](../debugger/includes/win8_md.md)] o versione successiva, impostare `RequiredPlatformVersion` a 6.2.0. Per specificare un modello per [!INCLUDE[win81](../debugger/includes/win81_md.md)] o versione successiva, impostare `RequiredPlatformVersion` alla versione 6.3.0.

 I modelli che specificano `RequiredPlatformVersion`= 8 compatibili con il cliente precedente [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] modelli.

 Elemento VSTemplate TemplateData... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Sintassi

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nessuno.

### <a name="attributes"></a>Attributi
 Nessuno.

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Specifica la piattaforma a cui è destinato il modello di progetto.|

## <a name="text-value"></a>Valore di testo
 È necessario specificare un valore di testo.

## <a name="remarks"></a>Note
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
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)