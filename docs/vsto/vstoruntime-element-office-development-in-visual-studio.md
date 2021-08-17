---
title: '&lt;Elemento vstoRuntime &gt; (Office sviluppo in Visual Studio)'
titleSuffix: ''
description: L'elemento vstoRuntime dello spazio dei nomi vstav3 contiene una versione supportata del runtime Visual Studio Tools per Office per una soluzione Office specifica.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1ce97744f8b7fc93317c80755b01ede222df2a4b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025641"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;Elemento vstoRuntime &gt; (Office sviluppo in Visual Studio)
  L'elemento `vstoRuntime` dello spazio dei nomi `vstav3` contiene una versione supportata del runtime di Visual Studio Tools per Office per una soluzione Office specifica.

## <a name="syntax"></a>Sintassi

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `vstoRuntime` è obbligatorio e si trova nello spazio dei nomi `vstav3` . Se una soluzione Office supporta due versioni del runtime di Visual Studio Tools per Office, nel manifesto dell'applicazione sono presenti due elementi `vstoRuntime` .

 L'elemento `vstoRuntime` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`release`|Obbligatorio. La versione di rilascio del runtime di Visual Studio Tools per Office.|
|`version`|Obbligatorio. Numero di versione del runtime di Visual Studio Tools per Office.|
|`supportUrl`|facoltativo. Collegamento alla posizione di installazione del runtime di Visual Studio Tools per Office.|

 `vstoRuntime` non contiene elementi.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra l'elemento `vstoRuntime` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Vedi anche

- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
