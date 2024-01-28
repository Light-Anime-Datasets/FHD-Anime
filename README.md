# FHD Anime Dataset

This repo contains datasets
for a large majority of native FHD anime,
intended to be used for neural network model training.

This repository only contains small sample sizes.
For the full sample size,
please refer to releases section.
A torrent will be available there
and be updated with every new addition.

This repository is divided into digital productions and film scans.
Please check the list below
for all the anime included in this dataset.
We also occasionally include notes that may be useful
depending on the type of model you're training.

## Known FHD anime

| Anime name                                            | In dataset | Digital/cel | Notes         |
| ----------------------------------------------------- | ---------- | ----------- | ------------- |
| Assault Lily: Bouquet                                 | Yes        | Digital     | Heavy banding |
| Clockwork Planet                                      | No         | Digital     |               |
| Full Metal Panic! Invisible Victory                   | No         | Digital     |               |
| Hai to Gensou no Grimgar                              | Yes        | Digital     | Grainy        |
| Keijo!!!!!!!!                                         | Yes        | Digital     |               |
| Renmei Kuugun Koukuu Mahou Ongakutai Luminous Witches | Yes        | Digital     |               |
| RWBY: Ice Queendom                                    | Yes        | Digital     |               |
| Violet Evergarden                                     | Yes        | Digital     |               |

For a list of checked
and excluded productions,
please refer to the [EXCLUDED.md](./EXCLUDED.md) file.

## Determining sources

There are a handful of considerations to take into account when selecting sources:

The first is cleanliness.
Even if the source image has a native resolution of N x 1080,
it's useless if it's starved or post-processed,
and has no business being used for training
where high quality "ground truths" are to be expected.

The second is whether a source is truly FHD.
Datasets exist currently that include mostly non-FHD sources,
presumed to be improperly determined
by looking at exclusively image's sharpness.
As a result, many datasets touting to use FHD anime datasets
are contaminated with below-native FHD anime instead,
such as BOCCHI THE ROCK (~873p),
or downsampled native 4k content,
such as Sol Levante.

We use three metrics to determine whether a show is native FHD:

1. Using our eyes.
   Upsampling often comes with a myriad of artifacting,
   such as ringing, blur, or antialiasing.
   A simple understanding of how these artifacts form and what they look like
   can immediately disqualify a large number of potential samples.
2. The [dft-view] plugin for [vspreview].
   This gives us an overview of the frequencies of an image.
   Very similar to the method [Anibin] used.
3. The [native-res] plugin for [vspreview].
   This also works with frequencies,
   but gives us a plot of results to look at,
   as well as other helpers for narrowing down native resolutions.

## How are images exported?

At the time of writing,
we use [lvsfunc.export_png][export-png]
to export png files.
The chroma planes are upscaled using Lanczos (3 taps),
and we pick one random frame in 15-second intervals.

We only ever use the highest quality source available at the time.
This will usually be the blu-ray,
but other, better sources
may also be used if available.

## Contribute

We accept contributions in the form of shows to check out.
If you know of any native FHD anime that are not listed above
(and you have done some rudimentary testing yourself),
please leave an issue.

Before leaving an issue,
please double-check that we have not looked at your anime yet,
and that it's likely to be a native FHD production.
Consistent wrongful issues may result in a ban.

We also welcome issues
that help slim down the dataset
by removing redundant frames,
or frames that make for poor training data.
If possible,
please include a list of frames
that you believe should be removed,
and we'll look at them.

If you'd like to get into direct contact with me,
please join the [Jaded Encoding Thaumaturgy discord server][discord].

## Additional resources

Here are a list of additional resources that (mostly accurately) document native FHD sources:

<!-- "mostly" because the AB collage has SAOA lol. -->

-   [Anibin]
-   [AnimeBytes]'s "Produced at 1080p" collage

<!-- References and other urls -->

[vspreview]: https://github.com/Jaded-Encoding-Thaumaturgy/vs-preview
[dft-view]: https://github.com/Jaded-Encoding-Thaumaturgy/vs-preview-plugins/tree/master/dft-view
[native-res]: https://github.com/Jaded-Encoding-Thaumaturgy/vs-preview-plugins/tree/master/native-res
[export-png]: https://github.com/Jaded-Encoding-Thaumaturgy/lvsfunc/blob/export-png/lvsfunc/export.py#L19-L120
[anibin]: https://anibin.blogspot.com/
[AnimeBytes]: https://animebytes.tv/collage.php?id=522
[discord]: https://discord.gg/2knZXNC5Qx
