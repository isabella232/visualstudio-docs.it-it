---
title: '&lt;&gt;elemento compatibleFrameworks (distribuzione ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675421"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;elemento compatibleFrameworks (distribuzione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica le versioni di .NET Framework in cui è possibile installare ed eseguire questa applicazione.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) non supporta l' `compatibleFrameworks` elemento quando si salva un manifesto dell'applicazione che è già stato firmato con un certificato utilizzando [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). È invece necessario usare [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
## <a name="syntax"></a>Sintassi  
  
```  
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
 L' `compatibleFrameworks` elemento è necessario per i manifesti di distribuzione destinati al [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Runtime fornito da [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] o versione successiva. L' `compatibleFrameworks` elemento contiene uno o più `framework` elementi che specificano le versioni .NET Framework in cui l'applicazione può essere eseguita. Il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] runtime eseguirà l'applicazione sul primo disponibile `framework` nell'elenco.  
  
 Nella tabella seguente sono elencati gli attributi `compatibleFrameworks` supportati dall'elemento.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`S` `upportUrl`|facoltativo. Specifica un URL in cui è possibile scaricare la versione .NET Framework compatibile preferita.|  
  
## <a name="framework"></a>framework  
 Obbligatorio. Nella tabella seguente sono elencati gli attributi `framework` supportati dall'elemento.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`targetVersion`|Obbligatorio. Specifica il numero di versione del .NET Framework di destinazione.|  
|`profile`|Obbligatorio. Specifica il profilo della .NET Framework di destinazione.|  
|`supportedRuntime`|Obbligatorio. Specifica il numero di versione del runtime associato alla .NET Framework di destinazione.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un `compatibleFrameworks` elemento in un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto di distribuzione. Questa distribuzione può essere eseguita in [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] . Può anche essere eseguito su [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] perché è un superset di [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
