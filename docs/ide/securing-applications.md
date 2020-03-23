---
title: Security
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87f06746901baaaf14f91032f8968a0d99fc20c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595449"
---
# <a name="secure-applications"></a>Proteggere le applicazioni

È opportuno includere considerazioni sulla sicurezza in tutti gli aspetti dello sviluppo di applicazioni, dalla progettazione alla distribuzione. Iniziare eseguendo Visual Studio nel modo più sicuro possibile. Vedere [Autorizzazioni utente](../ide/user-permissions-and-visual-studio.md).

Per sviluppare applicazioni efficacemente sicure, è necessario acquisire familiarità con i concetti e le funzionalità relative alla sicurezza delle piattaforme per le quali si sviluppano le applicazioni. È inoltre necessario comprendere le tecniche di sicurezza del codice.

## <a name="code-for-security"></a>Codice per la sicurezza

La maggior parte degli errori di codifica che determinano vulnerabilità di sicurezza è dovuta a valutazioni errate degli sviluppatori rispetto all'input utente o a una conoscenza parziale della piattaforma per la quale si sviluppano le applicazioni.

- Nelle [linee guida di codifica sicura](/dotnet/standard/security/secure-coding-guidelines) vengono descritti i diversi metodi di progettazione del codice .NET per poter usare un sistema di sicurezza.
- Nelle [procedure di sicurezza consigliate per C++](/cpp/top/security-best-practices-for-cpp) sono contenute informazioni sugli strumenti di sicurezza e linee guida per gli sviluppatori C++.

## <a name="build-for-security"></a>Compilazione di codice per la sicurezza

La sicurezza è anche un aspetto importante del processo di compilazione. Alcuni passaggi aggiuntivi possono migliorare la sicurezza di un'app distribuita e impedire il reverse engineering non autorizzato, lo spoofing o altri tipi di attacchi:

- [Dotfuscator](dotfuscator/index.md) è gratuito e consente di proteggere gli assembly .NET da reverse engineering e uso non autorizzato, come ad esempio debugging non autorizzato.
- [La firma con nome sicuro](managing-assembly-and-manifest-signing.md) può essere usata per identificare in modo univoco i componenti software, impedendo così lo spoofing dei nomi.

## <a name="see-also"></a>Vedere anche

- [Sicurezza in .NET](/dotnet/standard/security/index)
- [Sicurezza di AzureAzure security](/azure/security/)
- [Windows 10 Mobile security guide](/windows/security/threat-protection/windows-10-mobile-security-guide) (Guida alla sicurezza di Windows 10 Mobile)
- [Apache Cordova platform security features](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017) (Funzionalità di sicurezza della piattaforma Apache Cordova)
- [Sicurezza di ASP.NET Core](/aspnet/core/security/?view=aspnetcore-2.1)
- [Sicurezza di Windows FormWindows Forms security](/dotnet/framework/winforms/windows-forms-security)
