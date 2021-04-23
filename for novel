import re
import csv

with open('d:\\text.txt', 'r', encoding='UTF-8') as f:
    text = f.read()

every_reply = re.findall('class="l_post l_post_bright j_l_post clearfix  "(.*?)class="p_props_tail props_appraise_wrap"',text,re.S)
result_list = []
username_list = re.findall('username="(.*?)"', text, re.S)
content_list = re.findall('j_d_post_content >(.*?)<', text, re.S)
reply_time_list = re.findall('class="tail-info">(2021.*?)<', text, re.S)
# for i in range(len(username_list)):
#     result = {'username': username_list[i],
#               'content': content_list[i],
#               'reply_time': reply_time_list[i]}
#     result_list.append(result)
for each in every_reply:
    result = {}
    result['username'] = re.findall('username="(.*?)"',each,re.S)[0]
    result['content'] = re.findall('class="d_post_content j_d_post_content " style="display:;">(.*?)</div>',each,re.S)
    result['reply_time'] = re.findall('class="tail-info">(2021.*?)<',each,re.S)
    result_list.append(result)
with open('d:\\tieba.csv', 'w', encoding='UTF-8') as f:
    writer = csv.DictWriter(f, fieldnames=['username', 'content', 'reply_time'])
    writer.writeheader()
    writer.writerows(result_list)
