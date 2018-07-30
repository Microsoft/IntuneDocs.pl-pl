---
title: Przechowywanie i przetwarzanie danych w usłudze Intune
description: Informacje o tym, w jaki sposób dane osobowe są przechowywane i przetwarzane w usłudze Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5f7c24775f03011bd936b22e41cfd318e92b5d64
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34474653"
---
# <a name="data-storage-and-processing-in-intune"></a>Przechowywanie i przetwarzanie danych w usłudze Intune

Gdy usługa Intune [zbierze dane](privacy-data-collect.md), przechowywanie i przetwarzanie tych danych przebiega w sposób opisany poniżej.

## <a name="storing-personal-data"></a>Przechowywanie danych osobowych

Wszystkie zebrane dane inne niż telemetryczne są przetwarzane za pośrednictwem usługi Intune i są przechowywane w jednej lub kilku z następujących lokalizacji przechowywania: 

- Usługi SQL Azure 
- Kolekcje niezawodności (sieć Service Fabric)  
- Usługa Azure Storage 

Dane telemetryczne (dzienniki usługi, dzienniki wydajności, błędy itd.), które są kluczowe w procesie monitorowania i świadczenia stabilnej usługi, są wysyłane do magazynów danych telemetrycznych firmy Microsoft.

### <a name="storage-locations"></a>Lokalizacje magazynów

Firma Microsoft oferuje i obsługuje usługi Intune w wielu regionach na całym świecie. Usługa Intune uwzględnia lokalizację przechowywania danych klienta wybraną przez administratora.

Aby uzyskać więcej informacji, zobacz [Microsoft Intune — gdzie są moje dane klienta?](For more information, see Microsoft Intune Where is my customer data?)

### <a name="personal-data-retention"></a>Przechowywanie danych osobowych

Na ogół dane osobowe są przechowywane przez usługę Intune przez trzydzieści dni po usunięciu użytkownika z zarządzania usługi Intune.

Dane telemetryczne zebrane w ramach używania usługi Intune są przechowywane przez maksymalnie trzydzieści dni.

Dzienniki inspekcji są przechowywane przez maksymalnie jeden rok.

## <a name="processing-personal-data"></a>Przetwarzanie danych osobowych

Usługa Intune przetwarza dane osobowe za pomocą systemów posiadających certyfikat ISO. Aby uzyskać więcej informacji, zobacz [Portal zaufania usług](https://www.microsoft.com/en-us/TrustCenter/stp).

### <a name="profiling-and-marketing"></a>Profilowanie i marketing

Usługa Microsoft Intune nie używa żadnych danych osobowych zebranych w ramach świadczenia usługi do celów profilowania ani do celów marketingowych. 

### <a name="restrict-processing-of-personal-data"></a>Ograniczanie przetwarzania danych osobowych

Aby ograniczyć przetwarzanie danych osobowych użytkownika, możesz usunąć konto tego użytkownika w następujący sposób:
1. Wyeksportowanie elektronicznej kopii danych osobowych użytkownika obejmującej następujące informacje:
    - Konta
    - Dane usługi
    - Skojarzone dzienniki
2. Usunięcie konta użytkownika i skojarzonych danych z usługi Intune.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej na temat tego, jak usługa Intune [zabezpiecza i udostępnia](privacy-data-secure-share.md) dane osobowe. 