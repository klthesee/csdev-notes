

1.远程调用，使用的rpc框架是feign。
使用方法：
1）远程服务：
用@FeignClient声明可以被远程调用 
声明api
~~~
@FeignClient(name = "mogu-admin", configuration = FeignConfiguration.class)
public interface AdminFeignClient {


    /**
     * 获取系统配置信息
     */
    @RequestMapping(value = "/systemConfig/getSystemConfig", method = RequestMethod.GET)
    public String getSystemConfig();

}
~~~

实际服务接口
~~~
@RequestMapping("/systemConfig")
@Slf4j
public class SystemConfigRestApi {

    @Autowired
    private SystemConfigService systemConfigService;

    @AuthorityVerify
    @ApiOperation(value = "获取系统配置", notes = "获取系统配置")
    @GetMapping("/getSystemConfig")
    public String getSystemConfig() {
        return ResultUtil.successWithData(systemConfigService.getConfig());
    }
}
~~~

2)调用服务：
启动类声明远程服务接口位置
@EnableFeignClients("com.moxi.mogublog.commons.feign")
像本地一样调用远程服务暴露的接口
@Autowired
private FileService fileService;