---
title: Elemento RequiredPlatformVersion (modelli di Visual Studio) Documenti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701489"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (modelli di Visual Studio)
Specifica la versione minima del sistema operativo necessaria per il corretto funzionamento del modello di progetto. Questo elemento viene usato per [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] i modelli di progetto che creano app.

 Il `RequiredPlatformVersion` valore viene confrontato direttamente con la versione del sistema operativo. Se `RequiredPlatformVersion` il è superiore alla versione del sistema operativo, il modello non viene visualizzato nella finestra di dialogo **Nuovo progetto** . Per specificare [!INCLUDE[win8](../debugger/includes/win8_md.md)] un modello `RequiredPlatformVersion` per o superiore, impostare su 6.2.0. Per specificare [!INCLUDE[win81](../debugger/includes/win81_md.md)] un modello `RequiredPlatformVersion` per o superiore, impostare su 6.3.0.

 I modelli `RequiredPlatformVersion`che specificano 8 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] sono compatibili con i modelli di cliente precedenti.

 VSTemplate TemplateData ..... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Sintassi

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 No.

### <a name="attributes"></a>Attributi
 No.

### <a name="child-elements"></a>Elementi figlio
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[TemplatePlatformName (NomePiattaforma Modello)](../extensibility/templatedata-element-visual-studio-templates.md)|Specifica la piattaforma a cui è destinato il modello di progetto.|

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
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
