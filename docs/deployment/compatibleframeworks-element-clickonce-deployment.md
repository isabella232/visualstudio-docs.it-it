---
title: '&lt;&gt;elemento compatibleFrameworks (distribuzione ClickOnce) | Microsoft Docs'
description: L'elemento compatibleFrameworks identifica le versioni del .NET Framework in cui l'applicazione può essere installata ed eseguita.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5da9819cd3df667be5e8fa04372684f82762c037
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383066"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;elemento compatibleFrameworks (distribuzione ClickOnce)
Identifica le versioni di .NET Framework in cui è possibile installare ed eseguire questa applicazione.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) non supporta l' `compatibleFrameworks` elemento quando si salva un manifesto dell'applicazione che è già stato firmato con un certificato utilizzando [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). È invece necessario usare [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="syntax"></a>Sintassi

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L' `compatibleFrameworks` elemento è necessario per i manifesti di distribuzione destinati al [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Runtime fornito da .NET Framework 4 o versione successiva. L' `compatibleFrameworks` elemento contiene uno o più `framework` elementi che specificano le versioni .NET Framework in cui l'applicazione può essere eseguita. Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] runtime eseguirà l'applicazione sul primo disponibile `framework` nell'elenco.

 Nella tabella seguente sono elencati gli attributi `compatibleFrameworks` supportati dall'elemento.

|Attributo|Descrizione|
|---------------|-----------------|
|`S` `upportUrl`|Facoltativa. Specifica un URL in cui è possibile scaricare la versione .NET Framework compatibile preferita.|

## <a name="framework"></a>framework
 Obbligatorio. Nella tabella seguente sono elencati gli attributi `framework` supportati dall'elemento.

|Attributo|Descrizione|
|---------------|-----------------|
|`targetVersion`|Obbligatorio. Specifica il numero di versione del .NET Framework di destinazione.|
|`profile`|Obbligatorio. Specifica il profilo della .NET Framework di destinazione.|
|`supportedRuntime`|Obbligatorio. Specifica il numero di versione del runtime associato alla .NET Framework di destinazione.|

## <a name="remarks"></a>Commenti

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato un `compatibleFrameworks` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto di distribuzione. Questa distribuzione può essere eseguita in [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . Può anche essere eseguito nel .NET Framework 4 perché è un superset di [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Vedere anche
- [Manifesto della distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)