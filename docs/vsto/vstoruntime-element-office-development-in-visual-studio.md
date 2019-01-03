---
title: '&lt;vstoRuntime&gt; elemento (sviluppo per Office in Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c5562bdfa8c9cce8e9490392ad81a7e2e697160c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930700"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime&gt; elemento (sviluppo per Office in Visual Studio)
  L'elemento `vstoRuntime` dello spazio dei nomi `vstav3` contiene una versione supportata del runtime di Visual Studio Tools per Office per una soluzione Office specifica.

## <a name="syntax"></a>Sintassi

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Gli elementi e attributi
 L'elemento `vstoRuntime` è obbligatorio e si trova nello spazio dei nomi `vstav3` . Se una soluzione Office supporta due versioni del runtime di Visual Studio Tools per Office, nel manifesto dell'applicazione sono presenti due elementi `vstoRuntime` .

 L'elemento `vstoRuntime` presenta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`release`|Obbligatorio. La versione di rilascio del runtime di Visual Studio Tools per Office.|
|`version`|Obbligatorio. Numero di versione del runtime di Visual Studio Tools per Office.|
|`supportUrl`|Facoltativo. Collegamento alla posizione di installazione del runtime di Visual Studio Tools per Office.|

 `vstoRuntime` non contiene elementi.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra l'elemento `vstoRuntime` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice è parte di un esempio più esaustivo disponibile nel [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Vedere anche

- [Manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti della distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
