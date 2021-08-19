---
title: '&lt;Elemento customErrorReporting &gt; (ClickOnce Deployment) | Microsoft Docs'
description: L'elemento customErrorReporting specifica un URI da visualizzare quando si verifica un errore anziché una finestra di dialogo di errore che mostra lo stack di eccezioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b296e87accb896f25fe1d83d859e46b0e1d89755
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153758"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;Elemento customErrorReporting &gt; (ClickOnce distribuzione)
Specifica un URI da visualizzare quando si verifica un errore.

## <a name="syntax"></a>Sintassi

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Osservazioni
 Questo elemento è facoltativo. Senza di essa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] visualizza una finestra di dialogo di errore che mostra lo stack di eccezioni. Se `customErrorReporting` l'elemento è presente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] visualizza invece l'URI indicato dal `uri` parametro . L'URI di destinazione includerà la classe di eccezione esterna, la classe di eccezione interna e il messaggio di eccezione interna come parametri.

 Usare questo elemento per aggiungere funzionalità di segnalazione errori all'applicazione. Poiché l'URI generato include informazioni sul tipo di errore, il sito Web può analizzare le informazioni e visualizzare, ad esempio, una schermata di risoluzione dei problemi appropriata.

## <a name="example"></a>Esempio
 Il frammento di codice seguente `customErrorReporting` illustra l'elemento , insieme all'URI generato che potrebbe produrre.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>Vedi anche
- [ClickOnce manifesto della distribuzione](../deployment/clickonce-deployment-manifest.md)