---
title: Supporto di Visual Studio per FIPS
titleSuffix: ''
description: Informazioni su come Visual Studio supporta la modalità di funzionamento approvata per la pubblicazione Federal Information Processing Standard 140-2 per Windows, Azure e .NET.
ms.custom: SEO-VS-2020
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ddf7831df3a820c757120159d6d367b884d224a4
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597483"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Supporto di Visual Studio per la modalità di funzionamento di FIPS 140-2 approvata

A partire dalla [versione 16,4](/visualstudio/releases/2019/release-notes-v16.4/), Visual Studio 2019 supporta la pubblicazione Federal Information Processing Standard (FIPS) 140-2 modalità di funzionamento approvata per Windows, Azure e .NET. Con la [versione 16,5](/visualstudio/releases/2019/release-notes-archive-v16.5), Visual Studio supporta ora la modalità operativa di FIPS 140-2 approvata quando si sviluppano [applicazioni C++ destinate a un sistema Linux remoto](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/).

Per configurare la modalità di funzionamento approvato FIPS 140-2 per Visual Studio, [installare .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) e quindi abilitare l'impostazione criteri di gruppo, **crittografia di sistema: usa algoritmi conformi a FIPS per crittografia, hash e firma**.

Per ulteriori informazioni sulla modalità di funzionamento approvata FIPS 140-2 e su come abilitarla, vedere [fips 140-2 Validation](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Gli strumenti usati per sviluppare app per piattaforme non Microsoft come iOS o Android potrebbero non usare algoritmi conformi a FIPS. Il software di terze parti incluso in Visual Studio o nelle estensioni installate potrebbe non utilizzare algoritmi conformi a FIPS. E, lo sviluppo per le soluzioni [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) non supporta la modalità operativa di FIPS 140-2 approvata.

## <a name="next-steps"></a>Passaggi successivi

Per ulteriori informazioni sulla modalità di funzionamento approvato FIPS 140-2 per Visual Studio e per altri prodotti e servizi Microsoft, vedere i collegamenti seguenti:

- [Visual Studio: configurare lo sviluppo Linux remoto sicuro conforme a FIPS con C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: crittografia di sistema e utilizzo di algoritmi conformi a FIPS per crittografia, hash e firma](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: conformità FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Vedere anche

[Proteggere le applicazioni](securing-applications.md)