# ChangeIt dataset

### [[Project Website :dart:]](https://data.ciirc.cvut.cz/public/projects/2022LookForTheChange/)&nbsp;&nbsp;&nbsp;[[Paper :page_with_curl:]](https://arxiv.org/abs/2203.11637)&nbsp;&nbsp;&nbsp;[[Code :octocat:]](https://github.com/soCzech/LookForTheChange)&nbsp;&nbsp;&nbsp;[ChangeIt Dataset :octocat:]

This repository contrains **ChangeIt** dataset from the CVPR'22 paper [Look for the Change: Learning Object States and State-Modifying Actions from Untrimmed Web Videos](https://arxiv.org/abs/2203.11637).

<img src="https://data.ciirc.cvut.cz/public/projects/2022LookForTheChange/resources/img/dragon_fruit1.svg" style="width:48%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://data.ciirc.cvut.cz/public/projects/2022LookForTheChange/resources/img/dragon_fruit2.svg" style="width:48%">


## Dataset structure
- `videos/category_name.csv`: List of YouTube video ids corresponding to given category.
  The second column represents relevance score _r_ for given video. Details on the score computation are in the paper.
- `annotations/category_name/video_id.fps1.csv`: Annotation for a given video (only test videos are annotated).
  The first column is time in seconds of the original video. The second column is the label id associated with a given second of the video.
- `labels.csv`: Mapping of label ids to human-readable labels.
- `categories.csv`: Mapping of category names to human-readable names.
  The last column is the centering hyper-parameter theta for each category (see the paper for details).


## Video download
We recommend using [youtube-dl](https://github.com/ytdl-org/youtube-dl) for download of the videos.
- To download the videos in reasonable quality, we suggest for example the following set of commands.
  ```shell
  CAT="apple"
  mkdir -p downloads/${CAT}
  sed -r -e 's#^#youtube-dl https://www.youtube.com/watch?v=#' \
         -e "s#,.*# -o 'downloads/${CAT}/%(id)s.%(ext)s' -f 'bestvideo[height<=480]'#" \
      videos/${CAT}.csv > downloads/${CAT}.sh
  sh ./downloads/${CAT}.sh
  ```
- Note, you may need to add `youtube-dl` to path by `export PATH=$PATH:/path/to/folder/with/youtube-dl`.

You can also request to download ChangeIt videos from our servers.
- Send an email to _tomas.soucek at cvut dot cz_ specifiing your name and affiliation. Please use your institutional email (i.e. not gmail, etc.).
- The resolution of all videos we provide is approximately 480p. The annotated videos are also available in their best resolution as downloaded from YouTube.


## References
Tomáš Souček, Jean-Baptiste Alayrac, Antoine Miech, Ivan Laptev, and Josef Sivic.
[Look for the Change: Learning Object States and State-Modifying Actions from Untrimmed Web Videos](https://arxiv.org/abs/2203.11637).
In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2022.

```bibtex
@inproceedings{soucek2022lookforthechange,
    title={Look for the Change: Learning Object States and State-Modifying Actions from Untrimmed Web Videos},
    author={Sou\v{c}ek, Tom\'{a}\v{s} and Alayrac, Jean-Baptiste and Miech, Antoine and Laptev, Ivan and Sivic, Josef},
    booktitle = {Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
    month = {June},
    year = {2022}
}
```

## Disclaimer
Note the distribution of identities and activities in the ChangeIt dataset may not be representative of the global human population and the diversity in society.
Please be careful of unintended societal, gender, racial and other biases when training or deploying models trained on this data.
More details are available in the [paper](https://arxiv.org/abs/2203.11637).


## Acknowledgements
The project was supported by the European Regional Development Fund under the project IMPACT (reg. no. CZ.02.1.01/0.0/0.0/15_003/0000468) and by the Ministry of Education, Youth and Sports of the Czech Republic through the e-INFRA CZ (ID:90140), the French government under management of Agence Nationale de la Recherche as part of the "Investissements d'avenir" program, reference ANR19-P3IA-0001 (PRAIRIE 3IA Institute), and Louis Vuitton ENS Chair on Artificial Intelligence. We would like to also thank Kateřina Součková and Lukáš Kořínek for their help with the dataset.

