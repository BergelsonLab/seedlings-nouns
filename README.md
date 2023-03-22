[![DOI](https://zenodo.org/badge/590978338.svg)](https://zenodo.org/badge/latestdoi/590978338)

# Annotated nouns from the SEEDLingS corpus

The Study of Environmental Effects on Developing Linguistic Skills (SEEDLingS) is an initiative to explain how infants' early linguistic and environmental input plays a role in their learning.
We focus on understanding how babies learn words between 6-to 18-months old from the visual, social, and linguistic world around them.
By looking at the complex environment that babies are exposed to, from their perspective, we can attempt to decode how the developing mind interprets and organizes the objects and words it faces.
SEEDLingS is unique in that it combines well-controlled studies in the lab that assess what words infants know, with in-the-home audio and video recordings of what words infants hear, and what they see when they hear these words.

<!-- Blurb above is from https://bergelsonlab.com/seedlings/index.html -->

All in-home video and audio recordings that were collected each month were hand-coded for concrete imageable nouns that were said in the vicinity of the child or by the child themselves.
This dataset consists of these annotations and additional related information in tabular form.
These tables have accompanying codebooks, which should provide enough information to understand the data.
For more details, we refer you to the [companion website][companion-website].

## Files

- `seedlings-nouns.csv` - Contains all the annotated tokens.
- `recordings.csv` - Contains information about each of audio/video recording sessions.
- `sub-recordings.csv` - If the audio recording was paused one or more times, we consider all the recorded audio as one *recording* consisting of several *sub-recordings*. 
  If the recording wasn't paused at any time, *sub-recording* is the same as *recording*.
  This file also contains local time when each sub-recording started and ended.
- `regions.csv` - The audio recordings for months 08 and above weren't annotated in full.
  This file contains information about the regions that were annotated.
  See [below](#audio-recording-regions) for information on the types of annotated regions.
- `*.codebook.csv` - For each table listed above, there is an associated codebook listing and describing the columns of the table.

## Glossary

- **recording_id** -  Unique recording ID - a combination of media type, child ID, and month, e.g., video_41_12.
                      There is a recording for each combination of values of these three variables, except for audio_17_06 and video_22_09.
- **month** - Both audio and video recordings were taken longitudinally, starting when the babies were 6 months old and continuing once a month for a total of 12 recordings per baby.
              We refer to the first recording as a month 06 recording, the second as a month 07 recording, and so on up to month 17.
              We also refer to all the month *nn* recordings from all the babies as month *nn* recordings.
- **seedlings-nouns** - Annotations of hand-coded concrete imageable nouns audible in the listened-to parts of the recordings.
                        Each instance of these nouns is referred to as a *token*.
- **recording** - A single audio/video recording session.
                  Each month, one audio and one video session were recorded.
- **sub-recordings** - If the audio recording was paused one or more times, we would consider all the recorded audio as one *recording* consisting of several uninterrupted *sub-recordings*. 
                       If the recording wasn't paused at any time, the *recording* contains a single "*sub-recording*".
- **region** - Refers to an interval of time in the audio *recording*.
- **compiled video** - Video collage compiled from footage from all of the cameras used in a given recording.
               
                    
## Audio recording regions

### Subregions

For months 08 and later, five hour-long regions in the audio recordings were selected and ranked on talkativeness by an algorithm for potential annotation.
We refer to these regions as *subregions*.
Coders were then asked to annotate the highest-ranked subregions: top 4 for month 08-13, top 3 for months 14-17.

In some cases, a subregion wouldn't be annotated in full because the baby fell asleep or it was too hard to hear language because the baby was in the car, etc., and that part was marked to be skipped.
In these cases, the subregion in question would effectively get shortened and/or split into two or more parts.
Only the regions corresponding to the annotated parts (in most cases, the whole subregion) within the subregions assigned to be annotated are listed in `regions.csv` as *subregions*.
Let's use the following two highest-ranked subregions as an example:

|recording_id|region_type|start  |end    |position|subregion_rank|
|------------|-----------|-------|-------|--------|--------------|
|Audio_32_14 |subregion  |6900000|9093990|1       |1             |
|Audio_32_14 |subregion  |9910180|10500000|1       |1             |
|Audio_32_15 |subregion  |4800000|8400000|1       |1             |

In the case of recording `Audio_32_14`, a part of the rank-1 subregion between 9093990 and 9910180 was marked to be skipped resulting in the subregion being split into two parts.
In the case of recording `Audio_32_15`, the whole rank-1 subregion was annotated in full, and thus it got just one row.

The goal was to annotate 4 hours of audio per month for months 08-13, and 3 hours of audio per month for months 14-17.
Since some subregions weren't annotated in full, coders selected additional parts of the recording to make up for the lost time: first, in the lower-ranked subregions, and, if that wasn't enough, outside the subregions.

### Top-3/top-4/surplus regions

In order to compare properties of the coded nouns across the months and subjects, one would need to identify comparable regions in all the recordings.
One way to do that is comparing the same time of the day intervals across the months and subjects as in Bergelson et al. (2019).
This can be done by using the time of the day information in `sub-recordings.csv`.
Another way is to compare the most talkative intervals across the months.
For the latter option, we identified the top 4 most talkative hours of annotated audio in each recording for months 06-13 and top-3 hours of audio per month for months 14-17.

For most of the recordings, top 3 and top 4 hours are the same as top 3 and top 4 subregions.
However, in cases where annotated time in some subregions didn't add up to 1 hour and time outside subregions was used to make up for that missing time,
top 3 and top 4 hours can additionally include those make-up regions.
That is why `regions.csv` contains both *subregions* and *top_3*/*top_4* regions even though they are duplicates of each other most of the time.

In some cases, there was more made up annotated time than 3 or 4 hours that were meant to be annotated.
We call the annotated regions above the intended 3 or 4 total annotated hours *surplus regions*.

## License

[Creative Commons Attribution 4.0 International License](LICENSE)

## Citation Information

If you use this dataset, please cite at least one of the following papers:

- Bergelson E, Amatuni A, Dailey S, Koorathota S, Tor S. (2018) Day by day, hour by hour: Naturalistic language input to infants. Developmental Science, e12715. doi: 10.1111/desc.12715
- Bergelson, Elika & N. Aslin, Richard. (2017). Nature and origins of the lexicon in 6-mo-olds. Proceedings of the National Academy of Sciences, 114, 201712966. doi: 10.1073/pnas.1712966114
- Bergelson, Elika (2017). Bergelson Seedlings HomeBank Corpus. doi:10.21415/T5PK6D

## References

Bergelson, E., Amatuni, A., Dailey, S., Koorathota, S., & Tor, S. (2019). Day by day, hour by hour: Naturalistic language input to infants. Developmental science, 22(1), e12715.


[companion-website]: https://app.gitbook.com/o/-LD2B3y79nAYcWKjWKTb/s/yWW9xT02ReGtv2AHaBSB/group-1/audio-files
