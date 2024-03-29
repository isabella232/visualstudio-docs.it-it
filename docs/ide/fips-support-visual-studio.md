---
title: Visual Studio supporto per FIPS
titleSuffix: ''
description: Informazioni su come Visual Studio la modalità di funzionamento approvata Federal Information Processing Standard publication 140-2 per Windows, Azure e .NET.
ms.custom: SEO-VS-2020
ms.date: 10/01/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 9e0e1200d01a7cec8524dacb0232b3f2fed44f3a
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431536"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Visual Studio supporto per la modalità di funzionamento approvata FIPS 140-2

A partire dalla [versione 16.4,](/visualstudio/releases/2019/release-notes-v16.4/)Visual Studio 2019 supporta la modalità di funzionamento approvata dalla pubblicazione 140-2 di Federal Information Processing Standard (FIPS) per Windows, Azure e .NET. Con la [versione 16.5,](/visualstudio/releases/2019/release-notes-v16.5)Visual Studio supporta ora la modalità di funzionamento approvata FIPS 140-2 quando si sviluppano applicazioni [C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)che hanno come destinazione un sistema Linux remoto.

Per configurare la modalità di funzionamento approvata da FIPS 140-2 per Visual Studio, installare [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) e quindi abilitare l'impostazione Criteri di gruppo Crittografia sistema: Usare algoritmi conformi a FIPS per **crittografia, hash e firma.**

Per altre informazioni sulla modalità di funzionamento approvata FIPS 140-2 e su come [abilitarla, vedere Convalida FIPS 140-2](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Gli strumenti che si usano per sviluppare app per piattaforme non Microsoft come iOS o Android potrebbero non usare algoritmi conformi a FIPS. Anche il software di terze parti Visual Studio o le estensioni installate potrebbero non usare algoritmi conformi a FIPS. Inoltre, lo sviluppo [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) soluzioni non supporta la modalità di funzionamento approvata FIPS 140-2.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulla modalità di funzionamento approvata da FIPS 140-2 per Visual Studio e per altri prodotti e servizi Microsoft, vedere i collegamenti seguenti:

- [Visual Studio: Configurare lo sviluppo sicuro di Linux sicuro conforme a FIPS con C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: Crittografia di sistema e uso di algoritmi conformi a FIPS per crittografia, hash e firma](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: conformità FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Vedi anche

[Proteggere le applicazioni](securing-applications.md)