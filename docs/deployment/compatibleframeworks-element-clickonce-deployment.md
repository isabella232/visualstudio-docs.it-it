---
title: '&lt;compatibleFrameworks&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df45e5bc3f9294ac1a53353ec784d83c9220f1cf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900960"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; elemento (distribuzione ClickOnce)
Identifica le versioni di .NET Framework in cui è possibile installare ed eseguire questa applicazione.  
  
> [!NOTE]
>  [*MageUI.exe* ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) non supporta la `compatibleFrameworks` elemento durante il salvataggio di un manifesto dell'applicazione che è già stato firmato con un certificato usando [ *MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). È invece necessario usare [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
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
 Il `compatibleFrameworks` elemento è obbligatorio per manifesti della distribuzione che hanno come destinazione il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fornita dal runtime [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] o versione successiva. Il `compatibleFrameworks` elemento contiene uno o più `framework` gli elementi che specificano le versioni di .NET Framework in cui è possibile eseguire questa applicazione. Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] runtime verrà eseguita l'applicazione in corrispondenza del primo disponibile `framework` in questo elenco.  
  
 La tabella seguente elenca l'attributo che la `compatibleFrameworks` supportato dall'elemento.  
  
|Attributo|Description|  
|---------------|-----------------|  
|`S` `upportUrl`|Facoltativo. Specifica un URL in cui può essere scaricata la versione di .NET Framework compatibile preferita.|  
  
## <a name="framework"></a>framework  
 Obbligatorio. Nella tabella seguente elenca gli attributi che il `framework` supportato dall'elemento.  
  
|Attributo|Description|  
|---------------|-----------------|  
|`targetVersion`|Obbligatorio. Specifica il numero di versione di .NET Framework di destinazione.|  
|`profile`|Obbligatorio. Specifica il profilo di .NET Framework di destinazione.|  
|`supportedRuntime`|Obbligatorio. Specifica il numero di versione del runtime associato alla destinazione .NET Framework.|  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un `compatibleFrameworks` elemento in un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto della distribuzione. Questa distribuzione può essere eseguita di [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Anche possibile eseguire nel [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] perché è un superset del [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```xml  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)