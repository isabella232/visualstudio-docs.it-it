---
title: '&lt;Elemento compatibleFrameworks &gt; (ClickOnce Deployment) | Microsoft Docs'
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: ed84d7f7ed60a95baba293a33059a05093400bbb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138933"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;Elemento compatibleFrameworks &gt; (distribuzione ClickOnce)
Identifica le versioni di .NET Framework in cui è possibile installare ed eseguire questa applicazione.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) non supporta l'elemento quando si salva un manifesto dell'applicazione che è già stato firmato con `compatibleFrameworks` un certificato usando [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). È invece necessario usare [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

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
 L'elemento è obbligatorio per i manifesti di distribuzione che hanno come destinazione il runtime fornito `compatibleFrameworks` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] da .NET Framework 4 o versione successiva. `compatibleFrameworks`L'elemento contiene uno o più elementi che `framework` specificano le .NET Framework in cui l'applicazione può essere eseguita. Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] runtime eseguirà l'applicazione nel primo oggetto `framework` disponibile in questo elenco.

 Nella tabella seguente sono elencati gli attributi supportati `compatibleFrameworks` dall'elemento .

|Attributo|Descrizione|
|---------------|-----------------|
|`S` `upportUrl`|facoltativo. Specifica un URL in cui è possibile scaricare la versione .NET Framework compatibile preferita.|

## <a name="framework"></a>framework
 Obbligatorio. Nella tabella seguente sono elencati gli attributi supportati `framework` dall'elemento .

|Attributo|Descrizione|
|---------------|-----------------|
|`targetVersion`|Obbligatorio. Specifica il numero di versione del .NET Framework.|
|`profile`|Obbligatorio. Specifica il profilo dell'oggetto di .NET Framework.|
|`supportedRuntime`|Obbligatorio. Specifica il numero di versione del runtime associato al .NET Framework.|

## <a name="remarks"></a>Commenti

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato `compatibleFrameworks` un elemento in un manifesto della [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Questa distribuzione può essere eseguita in [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . Può essere eseguito anche nel .NET Framework 4 perché è un superset di [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Vedi anche
- [ClickOnce di distribuzione](../deployment/clickonce-deployment-manifest.md)