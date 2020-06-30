---
title: '&lt;&gt;elemento vstoRuntime (sviluppo per Office in Visual Studio)'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 985afe50d7c6edcfdb34e2ca046f59c5f7b664a0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541882"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento vstoRuntime (sviluppo per Office in Visual Studio)
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
|`supportUrl`|Facoltativa. Collegamento alla posizione di installazione del runtime di Visual Studio Tools per Office.|

 `vstoRuntime` non contiene elementi.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra l'elemento `vstoRuntime` in un manifesto dell'applicazione per una soluzione Office distribuita con [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Questo esempio di codice fa parte di un esempio più ampio fornito nei [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

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
