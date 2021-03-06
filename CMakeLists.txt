cmake_minimum_required(VERSION 3.3)
project(satsuma2)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -lpthread -std=c++14 -O3 -w")

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "bin")

# Satsuma2 binaries
set(SOURCE_FILES_MATCHDUMP kmatch/matchdump.cc kmatch/matchresult.h kmatch/KMatch.h)
set(SOURCE_FILES_KMATCH kmatch/KMatch.cc kmatch/KMatch.h kmatch/matchresult.h)
set(SOURCE_FILES_MERGEXCORRMATCHES analysis/MergeXCorrMatches.cc base/StringUtil.cc analysis/DNAVector.cc base/FileParser.cc analysis/XCorrDynProg.cc analysis/SequenceMatch.cc util/mutil.cc)
set(SOURCE_FILES_MATCHESBYFEATURE analysis/MatchesByFeature.cc)
set(SOURCE_FILES_CHAINMATCHES analysis/ChainMatches.cc base/StringUtil.cc analysis/DNAVector.cc base/FileParser.cc analysis/XCorrDynProg.cc analysis/MatchDynProg.cc analysis/SequenceMatch.cc util/mutil.cc)
set(SOURCE_FILES_SATSUMASYNTENY2 analysis/SatsumaSynteny2.cc analysis/DNAVector.cc base/FileParser.cc util/mutil.cc analysis/CodonTranslate.cc analysis/SeqChunk.cc base/StringUtil.cc analysis/AlignProbability.cc analysis/WorkQueue.cc analysis/MatchDynProg.cc util/SysTime.cc analysis/SequenceMatch.cc analysis/GridSearch.cc)
set(SOURCE_FILES_HOMOLOGYBYXCORRSLAVE analysis/HomologyByXCorrSlave.cc analysis/ProbTable.cc analysis/DNAVector.cc base/FileParser.cc util/mutil.cc analysis/CrossCorr.cc analysis/CodonTranslate.cc analysis/SeqChunk.cc base/StringUtil.cc analysis/AlignProbability.cc)
set(SOURCE_FILES_HOMOLOGYBYXCORR tools/analysis/HomologyByXCorr.cc
tools/analysis/DNAVector.cc tools/base/FileParser.cc tools/util/mutil.cc
tools/analysis/CrossCorr.cc tools/analysis/CodonTranslate.cc
tools/analysis/SeqChunk.cc tools/base/StringUtil.cc
tools/analysis/AlignProbability.cc tools/analysis/MatchDynProg.cc
tools/analysis/SequenceMatch.cc tools/aligns/KmerAlignCore.cc)

add_executable(MatchDump ${SOURCE_FILES_MATCHDUMP})
add_executable(KMatch ${SOURCE_FILES_KMATCH})
add_executable(MergeXCorrMatches ${SOURCE_FILES_MERGEXCORRMATCHES})
add_executable(MatchesByFeature ${SOURCE_FILES_MATCHESBYFEATURE})
add_executable(ChainMatches ${SOURCE_FILES_CHAINMATCHES})
add_executable(SatsumaSynteny2 ${SOURCE_FILES_SATSUMASYNTENY2})
add_executable(HomologyByXCorrSlave ${SOURCE_FILES_HOMOLOGYBYXCORRSLAVE})
add_executable(HomologyByXCorr ${SOURCE_FILES_HOMOLOGYBYXCORR})

# tools from Satsuma
# below gives MSG_CONFIRM error on OSX - see JW comment in tools/utils/SComm.cc
set(SOURCE_FILES_COLAALIGNSATSUMA tools/analysis/ColaAlignSatsuma.cc tools/base/FileParser.cc tools/analysis/CrossCorr.cc tools/analysis/DNAVector.cc tools/analysis/MatchDynProg.cc tools/analysis/AlignProbability.cc tools/util/mutil.cc tools/analysis/RefineSatsuma.cc tools/analysis/SequenceMatch.cc tools/aligns/KmerAlignCore.cc tools/analysis/SeqChunk.cc tools/base/ThreadHandler.cc tools/src/AlignmentBlock.cc tools/analysis/CodonTranslate.cc tools/src/Cola/Cola.cc tools/src/Alignment.cc tools/src/Cola/NSaligner.cc tools/src/Cola/EditGraph.cc tools/src/Cola/AlignmentCola.cc tools/src/Cola/NSGAaligner.cc tools/src/Cola/SWGAaligner.cc tools/base/StringUtil.cc tools/util/SComm.cc)
set(SOURCE_FILES_BLOCKDISPLAYSATSUMA tools/analysis/BlockDisplaySatsuma.cc tools/analysis/DNAVector.cc tools/util/mutil.cc tools/base/FileParser.cc tools/base/StringUtil.cc)
set(SOURCE_FILES_CHROMOSOMEPAINT tools/visual/ChromosomePaint.cc tools/base/FileParser.cc tools/util/mutil.cc tools/base/StringUtil.cc tools/visual/Color.cc tools/visual/Eps.cc)
set(SOURCE_FILES_MICROSYNTENYPLOT tools/visual/MicroSyntenyPlot.cc tools/base/FileParser.cc tools/util/mutil.cc tools/analysis/SequenceMatch.cc tools/base/StringUtil.cc tools/visual/Eps.cc)
set(SOURCE_FILES_ORDERORIENTBYSYNTENY tools/analysis/OrderOrientBySynteny.cc tools/analysis/DNAVector.cc tools/util/mutil.cc tools/base/FileParser.cc tools/base/StringUtil.cc)
set(SOURCE_FILES_SATSUMATOFASTA tools/analysis/SatsumaToFasta.cc tools/base/FileParser.cc tools/analysis/DNAVector.cc tools/util/mutil.cc tools/base/CommandLineParser.h tools/base/StringUtil.cc)
set(SOURCE_FILES_REVERSESATSUMAOUT tools/analysis/ReverseSatsumaOut.cc tools/base/FileParser.cc tools/base/CommandLineParser.h tools/util/mutil.cc tools/base/StringUtil.cc)
set(SOURCE_FILES_CHROMOSEMBLE tools/analysis/Chromosemble.cc tools/base/FileParser.cc tools/util/mutil.cc tools/base/StringUtil.cc)
set(SOURCE_FILES_SATSUMATOGFF tools/analysis/SatsumaToGFF.cc tools/base/FileParser.cc tools/base/CommandLineParser.h tools/util/mutil.cc tools/base/StringUtil.cc)
set(SOURCE_FILES_FILTERGRIDSEEDS tools/analysis/FilterGridSeeds.cc tools/analysis/DNAVector.cc tools/analysis/SequenceMatch.cc tools/util/mutil.cc tools/base/FileParser.cc tools/aligns/KmerAlignCore.cc tools/base/CommandLineParser.h tools/base/StringUtil.cc)
set(SOURCE_FILES_SORTSATSUMA tools/analysis/SortSatsuma.cc tools/base/FileParser.cc tools/util/mutil.cc tools/base/StringUtil.cc)
set(SOURCE_FILES_MERGESCAFFOLDSBYSYNTENY tools/analysis/MergeScaffoldsBySynteny.cc tools/analysis/DNAVector.cc tools/util/mutil.cc tools/base/FileParser.cc tools/base/StringUtil.cc)

add_executable(ColaAlignSatsuma ${SOURCE_FILES_COLAALIGNSATSUMA})
add_executable(BlockDisplaySatsuma ${SOURCE_FILES_BLOCKDISPLAYSATSUMA})
add_executable(ChromosomePaint ${SOURCE_FILES_CHROMOSOMEPAINT})
add_executable(MicroSyntenyPlot ${SOURCE_FILES_MICROSYNTENYPLOT})
add_executable(OrderOrientBySynteny ${SOURCE_FILES_ORDERORIENTBYSYNTENY})
add_executable(SatsumaToFASTA ${SOURCE_FILES_SATSUMATOFASTA})
add_executable(ReverseSatsumaOut ${SOURCE_FILES_REVERSESATSUMAOUT})
add_executable(Chromosemble ${SOURCE_FILES_CHROMOSEMBLE})
add_executable(SatsumaToGFF ${SOURCE_FILES_SATSUMATOGFF})
add_executable(FilterGridSeeds ${SOURCE_FILES_FILTERGRIDSEEDS})
add_executable(SortSatsuma ${SOURCE_FILES_SORTSATSUMA})
add_executable(MergeScaffoldsBySynteny ${SOURCE_FILES_MERGESCAFFOLDSBYSYNTENY})
