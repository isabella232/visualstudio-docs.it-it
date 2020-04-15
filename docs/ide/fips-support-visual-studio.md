---
title: Supporto di Visual Studio per la modalità di funzionamento approvata FIPS 140-2
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06d147397a168bb78a31a8fbe6929d6c2184d080
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/15/2020
ms.locfileid: "81386449"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Supporto di Visual Studio per la modalità di funzionamento approvata FIPS 140-2

A partire dalla [versione 16.4,](/visualstudio/releases/2019/release-notes-v16.4/)Visual Studio 2019 supporta la modalità di funzionamento approvata FIPS (Federal Information Processing Standard) 140-2 per Windows, Azure e .NET. E, con la [versione 16.5](/visualstudio/releases/2019/release-notes-v16.5/), Visual Studio ora supporta la modalità di funzionamento approvata FIPS 140-2 quando si sviluppano applicazioni C , destinate a [un sistema Linux remoto.](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)

Per configurare la modalità operativa approvata FIPS 140-2 per Visual Studio, [installare .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) e quindi abilitare l'impostazione di Criteri di gruppo Crittografia di **sistema: utilizza algoritmi FIPS compatibili per crittografia, hash e firma**.

Per ulteriori informazioni sulla modalità operativa approvata FIPS 140-2 e su come abilitarla, vedere [Convalida FIPS 140-2](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Gli strumenti utilizzati per sviluppare app per piattaforme non Microsoft come iOS o Android potrebbero non usare algoritmi compatibili con FIPS. Software di terze parti incluso in Visual Studio o le estensioni installate potrebbero non utilizzare algoritmi FIPS compatibili. Inoltre, lo sviluppo per le soluzioni [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) non supporta la modalità di funzionamento approvata FIPS 140-2.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulla modalità operativa approvata FIPS 140-2 per Visual Studio e per altri prodotti e servizi Microsoft, vedere i collegamenti seguenti:

- [Visual Studio: Configurare lo sviluppo Secure Linux compatibile con FIPS con C](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: crittografia di sistema e utilizzo di algoritmi FIPS compatibili per crittografia, hash e firma](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: conformità FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Vedere anche

[Proteggere le applicazioni](securing-applications.md)