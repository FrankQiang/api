FORMAT: 1A

# Lottery API Root [/]
Lottery API entry point

This resource get user lottery status and campaign id.

## Retrieve Lottery Entry Point [GET]

+ Response 200 (application/json)

        {
            'status': -1|0|1|2|3|4|5,
            'campaign_id': -1|1
        }

        status: 
            -1: 本日未抽奖
             0: 未抽中
             1: 中了，过了兑奖时间
             2: 中了，还未填写信息
             3: 中了，手机已验证
             4: 中了，已填写全部信息
             5: 活动已过期

        campaign_id:
            -1: 活动已过期
             1: 正在进行的活动id

## Lottery [/api/v1/lottery/{id}/]
Get bool judgement winning or not

+ Parameters 
    + id (integer) ... ID of the Lottery in the form of a hash.

### Retrieve lottery [GET]

+ Response 200 (application/json)

        {
            'status': True|False
        }

        status:
            True: winning
            False: not winning

## Send Valid Code [/api/v1/verify/?mobile=15513149587]
Send a code to mobile

+ Parameters
    + mobile(string) ... 

### Retrieve valid code [GET]

+ Response 200 (application/json)

        {
            'status': True|False
        }

        status:
            True: send ok
            False: send false

## Valid Code [/api/v1/verify/]
Valid mobile code 

### Retrieve Valid [PUT]

+ Request (application/json)

    + Body
            {
                'mobile': '15513149587', 
                'code': '123456'
            }

+ Response 204 (application/json)

        {
            'status': True|False
        }

        status:
            True: valid success
            False: valid false

## Add information [/api/v1/information/]
Add user name and address.

### Retrieve information [PUT]

+ Request (application/json)

        {
            'mobile: '15513149587', 
            'name': 'mary',
            'address': '南京'
        }

+ Response 204 (application/json)

        {
            'status': True|False
        }

        status:
            True: valid success
            False: put false

## Campaign Rulers [/api/v1/info/{id}/]
Get Campaign rulers

### Retrieve Campaign info [GET]

+ Response 200 (application/json)

        {
            'campaign': 
                {
                    'title': '2016',
                    'theme': 'apple',
                    'start_time': '2016-01-28T05:36:42Z',
                    'end_time': '2016-02-02T05:36:47Z',
                    'rulers': 'one day one time'
                }
            'awards':
                {
                    [
                        'name': 'iphone',
                        'amount': 100,
                        'link': 'http://www.shanbay.com/iphone.jpg'
                    ]
                    ...
                }
        }


