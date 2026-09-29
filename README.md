## Siddharth Ghosalkar
### Gameplay Mechanics & Systems Engineer specializing in UE5 (C++), Networked Multiplayer, and AWS Cloud Backends

First-class Games Development graduate from the University for the Creative Arts specializing in high-performance Unreal Engine 5 (C++) and networked multiplayer architecture. Experienced in designing modular component-driven frameworks, server-client replication, and scalable cloud backends via AWS. Adept at bridging technical systems design with multi-disciplinary production timelines—from rapid prototyping to final outcome.

<iframe width="560" height="315" src="https://www.youtube.com/embed/c51VBGlofx0?si=tuZV1aIdwmRSkHsF" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

[Play]( https://siddplus.itch.io/evolved-survivors)

```cpp
void ATheGameMode::StartRound()
{
    ATheGameState* GS = GetGameState<ATheGameState>();
    if (!GS) return;

    if (GS->CurrentRoundNumber == 1)
    {
        GS->bIsRunActive = true;
    }

    TArray<AActor*> FoundSpawners;
    UGameplayStatics::GetAllActorsOfClass(GetWorld(), AEnemySpawner::StaticClass(), FoundSpawners);
    for (AActor* Actor : FoundSpawners)
    {
        if (AEnemySpawner* Spawner = Cast<AEnemySpawner>(Actor))
            CachedSpawners.Add(Spawner);
    }

    GS->RoundTimer = BaseRoundDuration;
    GS->bIsRoundActive = true;
    GS->OnRep_IsRoundActive();

    for (AEnemySpawner* Spawner : CachedSpawners)
    {
        Spawner->ConfigureSpawner(CurrentRoundSpawnRate, CurrentRoundMaxEnemies, TargetHealthMult, TargetSpeedMult);
        Spawner->StartSpawningTimer();
    }

    GetWorldTimerManager().SetTimer(RoundTimerHandle, this, &ATheGameMode::AdvanceTimer, 1.0f, true);
}

```

Learn more about me: https://siddplus.github.io/Portfolio-Website/

Contact me: sidd.ghosalkar@outlook.com
