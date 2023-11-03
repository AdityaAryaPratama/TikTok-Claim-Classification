# TikTok-Claim-Classification

# Bussiness Problem Understanding
## Context

TikTok users have the ability to report videos and comments that contain user claims. These reports identify content that needs to be reviewed by moderators. This process generates a large number of user reports that are difficult to address quickly. 


TikTok is working on the development of a predictive model that can determine whether a video contains a claim or offers an opinion. Videos that are labeled opinions will be less likely to go on to be reviewed by a human moderator. Videos that are labeled as claims will be further sorted by a downstream process to determine whether they should get prioritized for review. 

With a successful prediction model, TikTok can reduce the backlog of user reports and prioritize them more efficiently.

## Goals

We wants to build a machine learning model to help identify claims and opinions. Videos that are labeled opinions will be less likely to go on to be reviewed by a human moderator. Videos that are labeled as claims will be further sorted by a downstream process to determine whether they should get prioritized for review. For example, perhaps videos that are classified as claims would then be ranked by how many times they were reported, then the top x% would be reviewed by a human each day.

A machine learning model would greatly assist in the effort to present human moderators with videos that are most likely to be in violation of TikTok's terms of service.

## Evaluation Metric

The evaluation metrics such as ROC AUC score, recall, precision, and F1-score are commonly used for classification tasks. Each metric provides a different perspective on how well your model is performing. To determine which evaluation metric might be best, consider how the model might be wrong. There are two possibilities for bad predictions:

- **False positives:** When the model predicts a video is a claim when in fact it is an opinion
- **False negatives:** When the model predicts a video is an opinion when in fact it is a claim

In the given scenario, it's better for the model to predict false positives when it makes a mistake, and worse for it to predict false negatives. It's very important to identify videos that break the terms of service, even if that means some opinion videos are misclassified as claims. The worst case for an opinion misclassified as a claim is that the video goes to human review. The worst case for a claim that's misclassified as an opinion is that the video does not get reviewed _and_ it violates the terms of service. A video that violates the terms of service would be considered posted from a "banned" author, as referenced in the data dictionary.

Because it's more important to minimize false negatives, the model evaluation metric will be **recall**. Also **Receiver Operating Characteristic** and **The Area Under the Curve** to evaluate the model's ability to distinguish between the classes.

# Data Understanding
### Attribute Information

| Attribute | Data Type, Length | Description |
| --- | --- | --- |
| # | int | TikTok assigned number for video with claim/opinion. |
| claim_status | obj | Whether the published video has been identified as an “opinion” or a “claim.” In this dataset, an “opinion” refers to an individual’s or group’s personal belief or thought. A “claim” refers to information that is either unsourced or from an unverified source. |
| video_id | int | Random identifying number assigned to video upon publication on TikTok. |
| video_duration_sec | int | How long the published video is measured in seconds. |
| video_transcription_text | obj | Transcribed text of the words spoken in the published video. |
| verified_status | obj | Indicates the status of the TikTok user who published the video in terms of their verification, either “verified” or “not verified.”  |
| author_ban_status | Text | Indicates the status of the TikTok user who published the video in terms of their permissions: “active,” “under scrutiny,” or “banned.”   |
| video_view_count | float | The total number of times the published video has been viewed.  |
| video_like_count | float | The total number of times the published video has been liked by other users.  |
| video_share_count | float | The total number of times the published video has been shared by other users.  |
| video_download_count | float | The total number of times the published video has been downloaded by other users.  |
| video_comment_count | float | The total number of comments on the published video. |

# Conclusion & Recommendation
## Conclusion

1. The model performed very well based on the result of both precision and F<sub>1</sub> that consistently high. in conclusion, the model successfully classified which videos are claims and opinions
2. Based on the features importance visualization, the most predictive features were all related to the metrics of a video. it was classifying based on all realted to engagement levels like views, shares, downloads of a video.

## Recommendation

1. To make a lot more better model, larger datasets are needed with a lot more various records in it.
2. New features are also needed for improvement such as user's followers which can be calculated to gain ER (Engagement Rates) from every users that post videos.
3. It would be helpful to have the number of times the video was reported. It would also be useful to have the total number of user reports for all videos posted by each author.## Recommendation
